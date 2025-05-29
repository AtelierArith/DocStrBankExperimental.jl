```julia
saveTree(treel)
saveTree(treel, filepath)

```

実験的、ベイズ（ジャンクション）ツリーオブジェクトをファイルに保存します。

ノート

  * `PackedBayesTreeNodeData` オブジェクトのセットを BSON 形式に変換して保存します。
  * IIF 問題 #481

関連

[`loadTree`](@ref), [`saveDFG`](@ref), [`loadDFG`](@ref), `BSON.@save`, `BSON.@load`
