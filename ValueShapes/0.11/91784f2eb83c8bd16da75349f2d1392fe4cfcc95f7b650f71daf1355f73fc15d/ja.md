```
ShapedAsNTArray{T<:NamedTuple,...} <: AbstractArray{T,N}
```

`AbstractArray{<:AbstractVector{<:Real},N}`を指定された[`NamedTupleShape`](@ref)に従って`NamedTuple`の配列として表示します。

`ShapedAsNTArray`は`Tables` APIを実装しています。

コンストラクタ:

```
ShapedAsNTArray(
    data::AbstractArray{<:AbstractVector{<:Real},
    shape::NamedTupleShape
)

shape.(data)
```

結果として得られる`ShapedAsNTArray`は`data`とメモリを共有します:

```julia
using ValueShapes, ArraysOfArrays, Tables, TypedTables

X = [
    (a = 42, b = rand(1:9, 2, 3))
    (a = 11, b = rand(1:9, 2, 3))
]

shape = valshape(X[1])
data = nestedview(Array{Int}(undef, totalndof(shape), 2))
Y = shape.(data)
@assert Y isa ShapedAsNTArray
Y[:] = X
@assert Y[1] == X[1] == shape(data[1])
@assert Y.a == [42, 11]
Tables.columns(Y)
@assert unshaped.(Y) === data
@assert Table(Y) isa TypedTables.Table
```

`unshaped.(Y)`を使用して`data`に直接アクセスします。

`Tables.columns(Y)`は列の`NamedTuple`を返します。これらは、各列のためにできるだけ連続したメモリレイアウトを使用してデータのコピーを含みます。
