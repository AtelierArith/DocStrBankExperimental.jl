```
ConleyMorseCM{T}
```

接続行列情報を構造体に集めます。

この構造体には以下のフィールドがあります：

  * `matrix::SparseMatrix{T}`: 接続行列
  * `columns::Vector{Int}`: 境界行列に対応する列
  * `poset::Vector{Int}`: 接続行列列のポセットインデックス
  * `labels::Vector{String}`: 接続行列列のラベル
  * `morse::Vector{Vector{String}}`: 元の複体におけるモース集合のベクトル
  * `conley::Vector{Vector{Int}}`: モース集合のためのコンリーインデックスのベクトル
  * `complex::LefschetzComplex`: レフシェッツ複体としてのコンリー複体
