Gauss-Lobatto IIIB-IIIB̄法のためのタブロー、s段

```julia
TableauLobattoIIIBIIIB̄(::Type{T}, s)
TableauLobattoIIIBIIIB̄(s) = TableauLobattoIIIBIIIB̄(Float64, s)
```

コンストラクタは、段数`s`とオプションでタブローの要素型`T`を受け取ります。

この [`PartitionedTableau`](@ref) は、`a` に [`TableauLobattoIIIB`](@ref) を、`ā` に [`TableauLobattoIIIB̄`](@ref) を使用します。
