```
read_fits_image(filename::String)
```

Read a FITS file and return the image, mappingParameters and the snapshot number.

# Returns

  * image: A 2D array with the image pixels
  * par:   mappingParameters used for the image
  * snap:  Number of the mapped snapshot
  * units: A unit string of the image

# Example

image, par, snap*nr, unit*string = read*fits*image(filename)
