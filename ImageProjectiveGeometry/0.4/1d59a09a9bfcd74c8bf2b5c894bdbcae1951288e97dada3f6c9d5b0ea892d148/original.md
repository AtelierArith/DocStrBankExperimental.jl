floatyx - Convert 2D ImageMeta to 2D float array with y x spatial order

```
Usage:  (fimg, prop) = floatyx(img)

Argument:  img - ::ImageMeta{T,2}

Returns:  fimg - ::Array{Float64,2} in "y" "x" spatial order.
          prop - A copy of the properties dictionary of the input image
                 with "spatialorder" adjusted (if this was needed).
```

Most image processing functions expect 2D arrays in (row, column) format and most feature localisation functions return corner and edge coordinates in terms of (row, column) coordinates.

This convenience function takes a 2D ImageMeta, extracts the data, converts it to a 2D Float64 array and, if necessary, transposes the data so that it is in "y" "x" (row, column) spatial order.  The ImageMeta spatial order property is set to ["y","x"] and the properties returned.
