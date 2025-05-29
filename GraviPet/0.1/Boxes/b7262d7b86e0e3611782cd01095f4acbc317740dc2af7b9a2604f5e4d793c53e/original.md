```
struct Box{D,T} <: Domain{SVector{D,T}}
```

A multi-dimensional [`Domains.Domain`](@ref), i.e. a box or hyper-rectangle.  The number of dimensions `D` must be a non-negative integer. `T` should be a real-valued scalar type such as `Float64`. The domain's element type is `SVector{D,T}`.

Zero-dimensional and one-dimensional domains are supported. Zero-dimensional domains contain only a single point (the origin). One-dimensional domains correspond to intervals (see [`Interval`](#GraviPet.Intervals.Interval)).
