```
pix_to_world(img::AstroImage, pixcoords; all=false)
```

Given an astro image, look up the world coordinates of the pixels given by `pixcoords`. World coordinates are resolved using WCS.jl and a WCSTransform calculated from any FITS header present in `img`. If no WCS information is in the header, or the axes are all linear, this will just return pixel coordinates.

`pixcoords` should be the coordinates in your current selection of the image. For example, if you select a slice like this:

```julia-repl
julia> cube = load("some-3d-cube.fits")
julia> slice = cube[10:20, 30:40, 5]
```

Then to look up the coordinates of the pixel in the bottom left corner of `slice`, run:

```julia-repl
julia> world_coords = pix_to_world(img, [1, 1])
[10, 30]
```

If WCS information was present in the header of `cube`, then those coordinates would be resolved using axis 1, 2, and 3 respectively.

To include world coordinates in all axes, pass `all=true`

```julia-repl
julia> world_coords = pix_to_world(img, [1, 1], all=true)
[10, 30, 5]
```

!! Coordinates must be provided in the order of `dims(img)`. If you transpose an image, the order you pass the coordinates should not change.
