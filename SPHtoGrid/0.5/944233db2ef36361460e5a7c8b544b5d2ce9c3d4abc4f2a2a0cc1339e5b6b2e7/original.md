```
read_allsky_fits_image(filename::String)
```

Read a FITS file containing an allsky image and returns the image, snapshot number and units.

# Returns

  * image: A 2D array with the image pixels
  * snap:  Number of the mapped snapshot
  * units: A unit string of the image

# Example

image, snap*nr, unit*string = read*allsky*fits_image(filename)
