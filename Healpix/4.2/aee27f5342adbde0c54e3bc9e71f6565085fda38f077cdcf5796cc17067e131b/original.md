```
project(invprojfn, m::HealpixMap{T, O, AA}, bmpwidth, bmpheight; kwargs...)
```

Return a 2D bitmap (array) containing a cartographic projection of the map and a 2D bitmap containing a boolean mask. The size of the bitmap is `bmpwidth`×`bmpheight` pixels. The function `projfn` must be a function which accepts as input two parameters `x` and `y` (numbers between -1 and 1).

The following keywords can be used in the call:

  * `center`: 2-tuple specifying the location (colatitude, longitude) of the sky point that is to be placed in the middle of the image (in radians)
  * `unseen`: by default, Healpix maps use the value -1.6375e+30 to mark unseen pixels. You can specify a different value using this keyword. This should not be used in common applications.

Return a `Array{Union{Missing, Float32}}` containing the intensity of each pixel. Pixels falling outside the projection are marked as NaN, and unseen pixels are marked as `missing`.
