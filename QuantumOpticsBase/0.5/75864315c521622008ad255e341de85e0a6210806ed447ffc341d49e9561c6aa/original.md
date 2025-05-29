```
directsum(x::Ket, y::Ket)
```

Construct a spinor via the [`directsum`](@ref) of two [`Ket`](@ref)s. The result is a [`Ket`](@ref) with data given by `[x.data;y.data]` and its basis given by the corresponding [`SumBasis`](@ref). **NOTE**: The resulting state is not normalized!
