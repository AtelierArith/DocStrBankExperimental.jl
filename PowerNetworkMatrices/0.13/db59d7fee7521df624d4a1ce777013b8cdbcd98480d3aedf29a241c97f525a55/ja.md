```julia
to_hdf5(ptdf, filename; compress, compression_level, force)

```

PTDFをHDF5ファイルにシリアライズします。

# 引数

  * `ptdf::PTDF`: 行列
  * `filename::AbstractString`: 作成するファイル
  * `compress::Bool`: 圧縮を有効にするかどうか、デフォルトはtrueです。
  * `compression_level::Int`: 圧縮が有効な場合に使用する圧縮レベル。
  * `force::Bool`: 既にファイルが存在する場合に上書きするかどうか、デフォルトはfalseです。
