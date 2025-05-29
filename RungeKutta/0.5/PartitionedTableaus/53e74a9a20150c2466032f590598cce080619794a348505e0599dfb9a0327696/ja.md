Gauss-Lobatto IIIF̄-IIIF法のためのタブロー s ステージ

```julia
TableauLobattoIIIF̄IIIF(::Type{T}, s)
TableauLobattoIIIF̄IIIF(s) = TableauLobattoIIIF̄IIIF(Float64, s)
```

コンストラクタは、ステージの数 `s` とオプションでタブローの要素型 `T` を受け取ります。

この [`PartitionedTableau`](@ref) は、`a` に対して [`TableauLobattoIIIF̄`](@ref) を、`ā` に対して [`TableauLobattoIIIF`](@ref) を使用します。
