```
beginprint(pathname)
```

Open and activate a print device.

**Parameters:**

`pathname` :     Filename for the print device.

`beginprint` opens an additional graphics output device. The device type is obtained from the given file extension. The following file types are supported:

```
+-------------+---------------------------------------+
|.ps, .eps    |PostScript                             |
+-------------+---------------------------------------+
|.pdf         |Portable Document Format               |
+-------------+---------------------------------------+
|.bmp         |Windows Bitmap (BMP)                   |
+-------------+---------------------------------------+
|.jpeg, .jpg  |JPEG image file                        |
+-------------+---------------------------------------+
|.png         |Portable Network Graphics file (PNG)   |
+-------------+---------------------------------------+
|.tiff, .tif  |Tagged Image File Format (TIFF)        |
+-------------+---------------------------------------+
|.fig         |Xfig vector graphics file              |
+-------------+---------------------------------------+
|.svg         |Scalable Vector Graphics               |
+-------------+---------------------------------------+
|.wmf         |Windows Metafile                       |
+-------------+---------------------------------------+
```
