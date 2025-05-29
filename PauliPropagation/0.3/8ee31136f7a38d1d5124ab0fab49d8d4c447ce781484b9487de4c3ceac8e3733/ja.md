```
function calculateptm(mat; tol=1e-15, heisenberg=true)
function calculateptm(dtype, mat; tol=1e-15, heisenberg=true)
```

行列 `mat` のパウリ転送行列 (PTM) を計算します。PTM はパウリ基底では実数値になりますが、一般的な基底では複素数になる可能性があります。エントリが浮動小数点数でない場合は、オプションのデータ型 `dtype` を渡します。PTM 内の小さな複素成分と絶対値は `tol` パラメータを使用して切り捨てます。デフォルトでは、PTM は -> ハイゼンベルク表現 <- で計算されます。つまり、PTM は行列の共役転置のものです。これは `heisenberg::Bool` キーワード引数を介して変更できます。引数

  * `mat::Matrix`: PTM が計算される進化ゲート行列。
  * `tol::Float64=1e-15`: PTM 内の小さな値を削除するための許容誤差。
  * `heisenberg::Bool=true`: PTM がハイゼンベルク表現で計算されるかどうか。
  * `dtype::DataType`: 実PTM のデフォルト型は `Float64` です。

戻り値

  * `ptm::Matrix`: 行列 `mat` の共役転置の PTM。
