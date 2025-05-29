```
photometry(::AbstractAperture, data::AbstractMatrix, [error])
photometry(::AbstractVector{<:AbstractAperture}, data::AbstractMatrix, [error])
```

Perform aperture photometry on `data` given aperture(s). If `error` (the pixel-wise standard deviation) is provided, will calculate sum error. If a list of apertures is provided the output will be a `TypedTables.Table`, otherwise a `NamedTuple`.

!!! tip
    This code is automatically multi-threaded. To take advantage of this please make sure `JULIA_NUM_THREADS` is set before starting your runtime.

