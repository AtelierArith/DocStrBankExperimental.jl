Gauss-Lobatto IIIC̄-IIIC法のためのタブロー（sステージ）

```julia
TableauLobattoIIIC̄IIIC(::Type{T}, s)
TableauLobattoIIIC̄IIIC(s) = TableauLobattoIIIC̄IIIC(Float64, s)
```

コンストラクタは、ステージの数`s`とオプションでタブローの要素型`T`を受け取ります。

この [`PartitionedTableau`](@ref) は、`a` に対して [`TableauLobattoIIIC̄`](@ref) を、`ā` に対して [`TableauLobattoIIIC`](@ref) を使用します。
