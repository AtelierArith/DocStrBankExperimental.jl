```
preview_dataset!(ax::PyObject, filename::String, label)
preview_dataset!(
            ax::PyObject,
            filename::String,
            label::String,
            format::FormatNC
)
```

データセットのプレビューを表示します。

  * `filename` プレビューするデータセットファイル
  * `label` プレビューするデータのラベル、NCファイルの変数名、TIFFファイルのバンド名
  * `format` [`AbstractFormat`](@ref) タイプファイルフォーマット
