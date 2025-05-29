パーティションされたガウス-ロバット IIIA-IIIB テーブルで s ステージ

```julia
TableauLobattoIIIAIIIB(::Type{T}, s)
TableauLobattoIIIAIIIB(s) = TableauLobattoIIIAIIIB(Float64, s)
```

コンストラクタは、ステージの数 `s` とオプションでテーブルの要素タイプ `T` を受け取ります。

この [`PartitionedTableau`](@ref) は、`a` に [`TableauLobattoIIIA`](@ref) を、`ā` に [`TableauLobattoIIIB`](@ref) を使用します。
