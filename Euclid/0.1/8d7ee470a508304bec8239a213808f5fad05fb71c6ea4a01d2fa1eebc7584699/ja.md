```julia
struct LineLoop{T, A<:(NTuple{N, T} where {N, T})} <: Euclid.AbstractGeometricPrimitive{T, 2}
```

  * `lines::NTuple{N, T} where {N, T}`
