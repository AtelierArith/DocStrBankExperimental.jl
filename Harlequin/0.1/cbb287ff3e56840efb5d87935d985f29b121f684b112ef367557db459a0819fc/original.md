```
genpointings!(sstr::ScanningStrategy, timerange_s, beam_dir, polangle_rad, result)
genpointings(sstr::ScanningStrategy, timerange_s, beam_dir, polangle_rad)
```

Generate a set of pointing directions and angles for a given orientation `beam_dir` (a 3-element vector) of the boresight beam, assuming the scanning strategy in `sstr`. The pointing directions are calculated over all the elements of the list `timerange_s`. The angle `polangle_rad` is the value of the polarization angle at time $t = 0$.

The two functions only differ in the way the result is returned to the caller. Function `genpointings` returns a N×6 matrix containing the following fields:

1. The colatitude (in radians)
2. The longitude (in radians)
3. The polarization angle (in radians)
4. The X component of the one-length pointing vector
5. The Y component
6. The Z component

Function `genpointings!` works like `genpointings`, but it accept a pre-allocated matrix as input (the `result` parameter) and will save the result in it. The matrix must have two dimensions with size `(N, 6)` at least.

Both functions are simple iterators wrapping [`time2pointing!`](@ref) and [`time2pointing`](@ref).
