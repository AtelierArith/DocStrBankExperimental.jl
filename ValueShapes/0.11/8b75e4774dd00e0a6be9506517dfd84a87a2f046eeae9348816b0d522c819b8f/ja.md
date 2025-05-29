```
unshaped(x)::AbstractVector{<:Real}
unshaped(x, shape::AbstractValueShape)::AbstractVector{<:Real}
```

xの構造化されたビュー（平坦/非構造化の実数値データベクトルに基づく[`AbstractValueShape`](@ref)）から、非構造化の基礎データを取得します。

`shape`が指定されている場合、xの形状がそれと互換性があることを保証します。xから正しい形状を推測できない場合、形状を指定する必要があるかもしれません。例えば、xが定数成分のために自由度が少ないと仮定される場合、xの単純な値から推測されるよりも少ない自由度を持つとされることがあります。

例:

```julia
shape = NamedTupleShape(
    a = ScalarShape{Real}(),
    b = ArrayShape{Real}(2, 3)
)
data = [1, 2, 3, 4, 5, 6, 7]
x = shape(data)
@assert unshaped(x, shape) == data
@assert unshaped(x.a) == view(data, 1:1)
@assert unshaped(x.b) == view(data, 2:7)
```
