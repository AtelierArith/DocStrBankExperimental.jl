```
projection(red::Reduction,s::AbstractArray) -> Projection
projection(red::Reduction,s::AbstractArray,X::MatrixOrTensor) -> Projection
```

Constructs a [`Projection`](@ref) from a collection of snapshots `s`. An inner product represented by the quantity `X` can be provided, in which case the resulting `Projection` will be `X`-orthogonal
