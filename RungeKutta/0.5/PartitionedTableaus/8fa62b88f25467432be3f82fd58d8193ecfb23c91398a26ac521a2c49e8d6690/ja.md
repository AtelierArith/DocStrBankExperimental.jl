Gauss-Lobatto IIIF-IIIF̄法のためのタブロー（sステージ）

```julia
TableauLobattoIIIFIIIF̄(::Type{T}, s)
TableauLobattoIIIFIIIF̄(s) = TableauLobattoIIIFIIIF̄(Float64, s)
```

コンストラクタは、ステージの数`s`とオプションでタブローの要素型`T`を受け取ります。

この [`PartitionedTableau`](@ref) は、`a` に [`TableauLobattoIIIF`](@ref) を、`ā` に [`TableauLobattoIIIF̄`](@ref) を使用します。
