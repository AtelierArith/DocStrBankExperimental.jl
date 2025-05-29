Gauss-Lobatto IIIE-IIIĒ法のためのタブロー（s段）

```julia
TableauLobattoIIIEIIIĒ(::Type{T}, s)
TableauLobattoIIIEIIIĒ(s) = TableauLobattoIIIEIIIĒ(Float64, s)
```

コンストラクタは、段数`s`とオプションでタブローの要素型`T`を受け取ります。

この [`PartitionedTableau`](@ref) は、`a` に [`TableauLobattoIIIE`](@ref) を、`ā` に [`TableauLobattoIIIĒ`](@ref) を使用します。
