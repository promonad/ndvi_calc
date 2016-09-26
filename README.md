# ndvi_calc
Python script for automation NDVI processing using landsat-util

---1. Getting started---

Landsat-util command line utility are working correctly only on linux systems, we recommend to use Ububntu 14.04 LTS:
http://www.ubuntu.com/download/alternative-downloads

Python 2.7 needed, preinstalled on Ubuntu OS.

You need to install following components:
-landsat-util;
-gdal-bin;
-python-gdal;
-urllib2.

Gdal-bin, python-gdal, urllib are available over APT, but landsat-util must be installed over PIP.

So lets install PIP with some science libraries:
$: sudo apt-get update
$: sudo apt-get install python-pip python-numpy python-scipy libgdal-dev libatlas-base-dev gfortran libfreetype6-dev

After that we will able to install landsat-util:
$: pip install landsat-util

For web publication in this pipeline we use Leaflet JS, so you may additionally to install and config Apache server software.

Copy ndvi_calc files and folders to Apache public folder (for publication on remote server) or copy to anywhere on your local computer.

---2. Chose your scene---

Landsat 8 follow WRS-2, so you must choose the proper scene according to this system.
Go to site: http://landsat.usgs.gov/worldwide_reference_system_WRS.php

Set paths and rows variables in script, line 36.

Set start date and end date for searching of imagery in line 36 (if you dont plan to automate it with cron).

---3. Start script---

Type in terminal (from the correct directory):
$: python ndvi.py
and wait when the operation will be finished.

Open index.html file and you will see result of NDVI processing on the map.

---4. Cron automation (optional)---

By default script check current day and saerch for the last available Landsat 8 image.
Add a daily script execution to cron, somthing like:

5 0 * * * $HOME/your_folder/ndvi.py >> $HOME/log/daily 2>&1
