```
Explanation(val, output, output_selection, analyzer, heatmap, extras)
```

[`analyze`](@ref)を呼び出すときのアナライザーの戻り値の型。

## フィールド

  * `val`: アナライザーの数値出力、例：アトリビューションまたは勾配
  * `output`: 指定されたアナライザー入力に対するモデル出力
  * `output_selection`: 説明に使用される出力のインデックス
  * `analyzer`: 使用されたアナライザーに対応するシンボル、例： `:Gradient` または `:LRP`
  * `heatmap`: プリセットのヒートマッピングスタイルを示すシンボル、例： `:attribution`、 `:sensitivity` または `:cam`
  * `extras`: アナライザーが追加情報を返すために使用できるオプションの名前付きタプル。
