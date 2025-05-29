```julia
abstract type NodalField{T, N, NF, NN, Vals} <: FiniteElementContainers.AbstractField{T, N, NF, Vals}
```

Abstract type for implementations of fields that live on nodes.

Constructors

`NodalField{NF, NN, Vector}(vals::M)                    where {NF, NN, M <: AbstractArray{<:Number, 2}}`

`NodalField{NF, NN, Matrix}(vals::M)                    where {NF, NN, M <: AbstractArray{<:Number, 2}}`

`NodalField{NF, NN, Vector}(vals::V)                    where {NF, NN, V <: AbstractArray{<:Number, 1}}`

`NodalField{NF, NN, Vector}(vals::V)                    where {NF, NN, V <: AbstractArray{<:Number, 1}}`

`NodalField{NF, NN, Vector, T}(::UndefInitializer)      where {NF, NN, T}`

`NodalField{NF, NN, Matrix, T}(::UndefInitializer)      where {NF, NN, T <: Number}`

`NodalField{NF, NN, StructArray, T}(::UndefInitializer) where {NF, NN, T}`

`NodalField{Tup, A, T}(::UndefInitializer)              where {Tup, A, T}`
