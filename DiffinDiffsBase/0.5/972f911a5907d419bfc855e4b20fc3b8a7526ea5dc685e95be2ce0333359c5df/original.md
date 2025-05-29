```
ScaledArray(x::AbstractArray, start, step[, stop]; reftype=Int32, usepool=true)
ScaledArray(x::AbstractArray, step; reftype=Int32, start, stop, usepool=true)
```

Construct a `ScaledArray` from `x` given the `step` size. If `start` or `stop` is not specified, it will be chosen based on the extrema of `x`.

# Keywords

  * `reftype::Type=Int32`: the element type of field `refs`.
  * `usepool::Bool=true`: find extrema of `x` based on `DataAPI.refpool`.
