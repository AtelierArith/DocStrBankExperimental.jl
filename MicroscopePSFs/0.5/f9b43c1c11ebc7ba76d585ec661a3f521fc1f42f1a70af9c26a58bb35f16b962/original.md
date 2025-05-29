```
get_pixel_size(camera::AbstractCamera)
```

Get the pixel size from camera geometry. Assumes uniform pixel size and square pixels.

Returns the pixel size in physical units (typically microns).

# Throws

  * AssertionError if pixels are not square
