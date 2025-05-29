```
prepare_plot!(index::AbstractDocumentIndex; verbose::Bool=true, kwargs...) -> AbstractDocumentIndex
```

指定されたドキュメントインデックスの2D UMAPプロットデータを準備します。

# 引数

  * `index`: プロットデータを準備するためのドキュメントインデックス。
  * `verbose`: INFOロギングを有効にするフラグ。

# 戻り値

  * `plot_data`フィールドが populatedされた更新されたインデックス。

# 例

```julia
index = build_index(["Some text", "More text"])
prepared_index = prepare_plot!(index)
```
