```julia
abstract type NodalField{T, N, NF, NN, Vals} <: FiniteElementContainers.AbstractField{T, N, NF, Vals}
```

ノード上に存在するフィールドの実装のための抽象型。

コンストラクタ

`NodalField{NF, NN, Vector}(vals::M)                    where {NF, NN, M <: AbstractArray{<:Number, 2}}`

`NodalField{NF, NN, Matrix}(vals::M)                    where {NF, NN, M <: AbstractArray{<:Number, 2}}`

`NodalField{NF, NN, Vector}(vals::V)                    where {NF, NN, V <: AbstractArray{<:Number, 1}}`

`NodalField{NF, NN, Vector}(vals::V)                    where {NF, NN, V <: AbstractArray{<:Number, 1}}`

`NodalField{NF, NN, Vector, T}(::UndefInitializer)      where {NF, NN, T}`

`NodalField{NF, NN, Matrix, T}(::UndefInitializer)      where {NF, NN, T <: Number}`

`NodalField{NF, NN, StructArray, T}(::UndefInitializer) where {NF, NN, T}`

`NodalField{Tup, A, T}(::UndefInitializer)              where {Tup, A, T}`
