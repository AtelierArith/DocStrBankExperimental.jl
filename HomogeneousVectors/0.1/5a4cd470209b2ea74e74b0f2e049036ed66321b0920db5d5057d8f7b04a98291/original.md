```
HomogeneousVector{T<:AbstractArray}
```

Or `HV{T}` shortly. A wrapper around a 3 long vector with type {T}. Multiplying it with a `StaticHomogeneousMatrix` or `MutableHomogeneousMatrix` return a 3 long vector with type {T}.
