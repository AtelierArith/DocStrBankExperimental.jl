```julia
abstract type ElementField{T, N, NN, NE, Vals} <: FiniteElementContainers.AbstractField{T, N, NN, Vals}
```

Abstract type for implementations of fields that live on elements.

Constructors

`ElementField{NN, NE, Vector}(vals::M)                    where {NN, NE, M <: AbstractArray{<:Number, 2}}`

`ElementField{NN, NE, Matrix}(vals::M)                    where {NN, NE, M <: AbstractArray{<:Number, 2}}`

`ElementField{NN, NE, Vector}(vals::V)                    where {NN, NE, V <: AbstractArray{<:Number, 1}}`

`ElementField{NN, NE, Vector, T}(::UndefInitializer)      where {NN, NE, T}`

`ElementField{NN, NE, Matrix, T}(::UndefInitializer)      where {NN, NE, T <: Number}`

`ElementField{NN, NE, StructArray, T}(::UndefInitializer) where {NN, NE, T}`

`ElementField{Tup, A, T}(::UndefInitializer)              where {Tup, A, T}`

`ElementField{Tup, A}(vals::M)                            where {Tup, A, M <: AbstractArray}`
