```
FrankenTuple{T<:Tuple, names, NT<:Tuple}
```

`FrankenTuple`は、型`T`の`Tuple`と、名前`names`と型`NT`を持つ`NamedTuple`を含みます。これは、部分的に名前が付けられたタプルのように、両者の間の交差のように機能します。

`FrankenTuple`の名前付き部分には`NamedTuple`を使用してアクセスでき、名前の付いていない部分には`Tuple`を使用してアクセスできます。

# 例

```jldoctest
julia> ft = FrankenTuple((1, 2), (a=1, b=2))
FrankenTuple((1, 2), (a = 1, b = 2))

julia> Tuple(ft)
(1, 2)

julia> NamedTuple(ft)
(a = 1, b = 2)
```
