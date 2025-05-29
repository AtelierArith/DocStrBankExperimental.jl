```julia
load_dataset(name; kwargs...)

```

データセット `dataset_name` をロードし、この順序でキーワード引数に応じて、中心化（平均を引く）、標準化（各属性をその標準偏差で割る）、そしてサンプルを再スケール（最大 ‖xᵢ‖₂ が 1.0 になるように）します。

キーワード引数には以下が含まれます：

  * center = false
  * standardize = false
  * rescale_columns = false

HDF5ベースのデータセットの場合、次のことも指定できます：

  * ncols = Inf: データセットに使用する列の数。

`ncols` を `center`、`standardize` または `rescale_columns` と一緒に使用する場合、データセットの統計は毎回再計算する必要があることに注意してください。
