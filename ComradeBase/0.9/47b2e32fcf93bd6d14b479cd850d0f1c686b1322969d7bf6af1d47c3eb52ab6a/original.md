```
imagepixels(fovx, fovy, nx, ny, x0=0, y0=0; posang=0.0, executor=Serial(), header=NoHeader())
```

Construct a grid of pixels with a field of view `fovx` and `fovy` and `nx` and `ny` pixels. This points are the pixel centers and the field of view goes from the edge of the first pixel to the edge of the last pixel. The `x0`, `y0` offsets shift the image origin over by (`x0`, `y0`) in the image plane.

## Arguments:

  * `fovx::Real`: The field of view in the x-direction
  * `fovy::Real`: The field of view in the y-direction
  * `nx::Integer`: The number of pixels in the x-direction
  * `ny::Integer`: The number of pixels in the y-direction

## Keyword Arguments:

  * `x0::Real=0`: The x-offset of the image
  * `y0::Real=0`: The y-offset of the image
  * `posang::Real=0`: The position angle of the grid, relative to RA=0 axis.
  * `executor=Serial()`: The executor to use for the grid, default is serial execution
  * `header=NoHeader()`: The header to use for the grid
