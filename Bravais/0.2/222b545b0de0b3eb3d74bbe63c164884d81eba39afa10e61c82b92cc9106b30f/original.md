```
dualbasis(Vs)
```

Return the dual (sometimes called the reciprocal) basis of a basis `Vs` in `D` dimensions.

The input basis `Vs` can be provided as:

  * a `D`-dimensional `StaticVector` of `AbstractVector`s,
  * a `D`-dimensional `NTuple` of `AbstractVector`s,
  * or, type-unstably, as any iterable of `AbstractVector`s.

If `Vs` a [`DirectBasis`](@ref), the type of the returned dual lattice is a [`ReciprocalBasis`](@ref) and vice versa. For other input types, the return type is an `SVector{D, <:SVector{D}}`.
