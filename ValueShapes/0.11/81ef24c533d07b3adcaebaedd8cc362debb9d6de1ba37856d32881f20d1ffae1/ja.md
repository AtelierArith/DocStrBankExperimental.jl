```
ShapedAsNT{names,...}
```

`AbstractVector{<:Real}` の可変名付きタプル（ただし、正確には `NamedTuple` ではない）としてのビューで、指定された [`NamedTupleShape`](@ref) に従います。

コンストラクタ:

```
ShapedAsNT(data::AbstractVector{<:Real}, shape::NamedTupleShape)

shape(data)
```

結果として得られる `ShapedAsNT` は `data` とメモリを共有します:

```julia
x = (a = 42, b = rand(1:9, 2, 3))
shape = NamedTupleShape(
    ShapedAsNT,
    a = ScalarShape{Real}(),
    b = ArrayShape{Real}(2, 3)
)
data = Vector{Int}(undef, shape)
y = shape(data)
@assert y isa ShapedAsNT
y[] = x
@assert y[] == x
y.a = 22
@assert shape(data) == y
@assert unshaped(y) === data
```

`unshaped(x)` を使用して `data` に直接アクセスします。

他に [`ShapedAsNTArray`](@ref) も参照してください。
