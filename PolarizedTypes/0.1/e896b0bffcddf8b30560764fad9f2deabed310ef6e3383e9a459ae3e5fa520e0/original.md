```julia
struct StokesParams{T} <: StaticArraysCore.FieldVector{4, T}
```

Static vector that holds the stokes parameters of a polarized complex visibility

To convert between a `StokesParams` and `CoherencyMatrix` use the `convert` function

```julia
convert(::CoherencyMatrix, StokesVector(1.0, 0.1, 0.1, 0.4))
```
