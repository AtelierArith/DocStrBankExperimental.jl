```julia
abstract type QuadratureField{T, N, NF, NQ, NE, Vals} <: FiniteElementContainers.AbstractField{T, N, NF, Vals}
```

Abstract type for implementations of fields that live on quadrature points.

Constructors

`QuadratureField{NF, NQ, NE, Matrix}(vals::Matrix{<:Number})      where {NF, NQ, NE}`

`QuadratureField{NF, NQ, NE, Vector}(vals::Matrix{<:Number})      where {NF, NQ, NE}`

`QuadratureField{NF, NQ, NE, Matrix, T}(::UndefInitializer)       where {NF, NQ, NE, T}`

`QuadratureField{NF, NQ, NE, StructArray, T}(::UndefInitializer)  where {NF, NQ, NE, T}`

`QuadratureField{NF, NQ, NE, StructVector, T}(::UndefInitializer) where {NF, NQ, NE, T}`

`QuadratureField{NF, NQ, NE, Vector, T}(::UndefInitializer)       where {NF, NQ, NE, T}`

`QuadratureField{Tup, A, T}(::UndefInitializer)                   where {Tup, A, T}`

`QuadratureField{Tup, A}(vals::M)                                 where {Tup, A, M <: AbstractArray}`
