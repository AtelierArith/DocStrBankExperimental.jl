```
reproject(input_data, output_projection; shape_out = nothing, order = 1, hdu_in = 1, hdu_out = 1)
```

Reprojects image data to a new projection using interpolation.

# Arguments

  * `input_data`: Image data which is being reprojected.               It can be an ImageHDU, FITS object, name of a FITS file or a tuple of image matrix and WCSTransform.
  * `output_projection`: Frame in which data is reprojected.                      Frame can be taken from WCSTransform object, ImageHDU, FITS or name of FITS file.
  * `shape_out`: Shape of image after reprojection.
  * `order`: Order of interpolation.          0: Nearest-neighbor          1: Linear          2: Quadratic
  * `hdu_in`: Used to specify HDU number when giving input as FITS or name of FITS file.
  * `hud_out:` Used to specify HDU number when giving output projection as FITS or name of FITS file.
