```
UncertainValue(data::Vector{T};
    kernel::Type{D} = Normal,
    npoints::Int=2048) where {D <: Distributions.Distribution, T}
```

Construct an uncertain value by a kernel density estimate to `data`.

Fast Fourier transforms are used in the kernel density estimation, so the number of points should be a power of 2 (default = 2048).
