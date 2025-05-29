Gauss-Lobatto IIIB-IIIA法のための台形

```julia
TableauLobattoIIIBIIIA(::Type{T}, s)
TableauLobattoIIIBIIIA(s) = TableauLobattoIIIBIIIA(Float64, s)
```

コンストラクタは、ステージの数`s`とオプションで台形の要素型`T`を受け取ります。

この [`PartitionedTableau`](@ref) は、`a` に [`TableauLobattoIIIB`](@ref) を、`ā` に [`TableauLobattoIIIA`](@ref) を使用します。
