```julia
abstract type ElementField{T, N, NN, NE, Vals} <: FiniteElementContainers.AbstractField{T, N, NN, Vals}
```

要素上に存在するフィールドの実装のための抽象型。

コンストラクタ

`ElementField{NN, NE, Vector}(vals::M)                    where {NN, NE, M <: AbstractArray{<:Number, 2}}`

`ElementField{NN, NE, Matrix}(vals::M)                    where {NN, NE, M <: AbstractArray{<:Number, 2}}`

`ElementField{NN, NE, Vector}(vals::V)                    where {NN, NE, V <: AbstractArray{<:Number, 1}}`

`ElementField{NN, NE, Vector, T}(::UndefInitializer)      where {NN, NE, T}`

`ElementField{NN, NE, Matrix, T}(::UndefInitializer)      where {NN, NE, T <: Number}`

`ElementField{NN, NE, StructArray, T}(::UndefInitializer) where {NN, NE, T}`

`ElementField{Tup, A, T}(::UndefInitializer)              where {Tup, A, T}`

`ElementField{Tup, A}(vals::M)                            where {Tup, A, M <: AbstractArray}`
