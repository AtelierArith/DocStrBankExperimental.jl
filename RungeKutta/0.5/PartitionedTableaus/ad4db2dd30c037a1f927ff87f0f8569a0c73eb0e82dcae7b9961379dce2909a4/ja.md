Gauss-Lobatto IIIG-IIIḠ法のためのタブロー（s段）

```julia
TableauLobattoIIIGIIIḠ(::Type{T}, s)
TableauLobattoIIIGIIIḠ(s) = TableauLobattoIIIGIIIḠ(Float64, s)
```

コンストラクタは、段数`s`とオプションでタブローの要素型`T`を受け取ります。

この [`PartitionedTableau`](@ref) は、`a` に対して [`TableauLobattoIIIG`](@ref) を、`ā` に対して [`TableauLobattoIIIḠ`](@ref) を使用します。
