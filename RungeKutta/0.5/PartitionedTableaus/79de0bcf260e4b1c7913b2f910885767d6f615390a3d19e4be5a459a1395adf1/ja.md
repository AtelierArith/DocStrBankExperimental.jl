Gauss-Lobatto IIIA-IIIĀ法のためのタブロー（sステージ）

```julia
TableauLobattoIIIAIIIĀ(::Type{T}, s)
TableauLobattoIIIAIIIĀ(s) = TableauLobattoIIIAIIIĀ(Float64, s)
```

コンストラクタは、ステージの数`s`とオプションでタブローの要素型`T`を受け取ります。

この [`PartitionedTableau`](@ref) は、`a` に対して [`TableauLobattoIIIA`](@ref) を、`ā` に対して [`TableauLobattoIIIĀ`](@ref) を使用します。
