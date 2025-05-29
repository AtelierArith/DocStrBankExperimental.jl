Gauss-Lobatto IIIC-IIIC̄法のためのタブロー（sステージ）

```julia
TableauLobattoIIICIIIC̄(::Type{T}, s)
TableauLobattoIIICIIIC̄(s) = TableauLobattoIIICIIIC̄(Float64, s)
```

コンストラクタは、ステージの数`s`とオプションでタブローの要素型`T`を受け取ります。

この [`PartitionedTableau`](@ref) は、`a` に対して [`TableauLobattoIIIC`](@ref) を、`ā` に対して [`TableauLobattoIIIC̄`](@ref) を使用します。
