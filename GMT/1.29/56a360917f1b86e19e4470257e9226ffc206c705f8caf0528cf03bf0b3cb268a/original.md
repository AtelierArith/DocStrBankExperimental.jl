```
R = rescale(A; low=0.0, up=1.0; inputmin=nothing, inputmax=nothing, stretch=false, type=nothing)
```

  * `A`: is either a GMTgrid, GMTimage, Matrix{AbstractArray} or a file name. In later case the file is read  with a call to `gmtread` that automatically decides how to read it based on the file extension ... not 100% safe.
  * `rescale(A)` rescales all entries of an array `A` to [0,1].
  * `rescale(A,low,up)` rescales all entries of A to the interval [low,up].
  * `rescale(..., inputmin=imin)` sets the lower bound `imin` for the input range. Input values less  than `imin` will be replaced with `imin`. The default is min(A).
  * `rescale(..., inputmax=imax)` sets the lower bound `imax` for the input range. Input values greater  than `imax` will be replaced with `imax`. The default is max(A).
  * `rescale(..., stretch=true)` automatically determines [inputmin inputmax] via a call to histogram that  will (try to) find good limits for histogram stretching. The form `stretch=(imin,imax)` allows specifying  the input limits directly.
  * `type`: Converts the scaled array to this data type. Valid options are all Unsigned types (e.g. `UInt8`).  Default returns the same data type as `A` if it's an AbstractFloat, or Float64 if `A` is an integer.

Returns a GMTgrid if `A` is a GMTgrid of floats, a GMTimage if `A` is a GMTimage and `type` is used or an array of Float32|64 otherwise.
