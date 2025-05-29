`imadjustintensity(img [, (minval,maxval)]) -> Image`

Map intensities over the interval `(minval,maxval)` to the interval    `[0,1]`. This is equivalent to `map(ScaleMinMax(eltype(img), minval,    maxval), img)`.  (minval,maxval) defaults to `extrema(img)`.
