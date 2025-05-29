```
cd_active!(X::AbstractArray{Float64,2}, Y::AbstractArray{Float64,2}, 
                Z::AbstractArray{Float64,2}, lambda::Float64, alpha::Float64,
                B::AbstractArray{Float64,2}, 
                regXidx::AbstractArray{Int64,1}, 
                regZidx::AbstractArray{Int64,1}, reg::BitArray{2}, norms; 
                isVerbose::Bool=true, stepsize::Float64=0.01, 
                isRandom::Bool=true, thresh::Float64=10.0^(-7), 
                maxiter::Int=10^10)
```

アクティブセットを利用して、ランダムまたは循環的な更新を使用して座標降下を実行します。

# 引数

  * X = 行の共変量からなる浮動小数点の2次元配列で、すべてのカテゴリ変数が適切なコントラストでコーディングされています
  * Y = 多変量応答からなる浮動小数点の2次元配列
  * Z = 列の共変量からなる浮動小数点の2次元配列で、すべてのカテゴリ変数が適切なコントラストでコーディングされています
  * lambda = ペナルティのラムダ、浮動小数点スカラー
  * alpha = L1とL2のペナルティの混合を決定するパラメータ (ϵ[0, 1])
  * B = 開始係数推定からなる浮動小数点の2次元配列
  * regXidx = 正則化されたX共変量に対応するインデックスの1次元配列
  * regZidx = 正則化されたZ共変量に対応するインデックスの1次元配列
  * reg = 各係数を正則化するかどうかを示すビットの2次元配列
  * norms = 各係数に対応するノルムからなる浮動小数点の2次元配列または`nothing`

# キーワード引数

  * isVerbose = メッセージを表示するかどうかを示すブールフラグ。デフォルトは`true`。
  * stepsize = 浮動小数点; 更新のステップサイズ（座標降下には無関係）。デフォルトは`0.01`。
  * isRandom = ランダムまたは循環的な更新を使用するかどうかを示すブールフラグ。デフォルトは`true`。
  * thresh = 係数が収束したと見なされる閾値、浮動小数点スカラー。デフォルトは`10^(-7)`。
  * maxiter = 更新の最大反復回数。デフォルトは`10^10`。

# 値

なし; 係数をその場で更新します

# 一部の注意事項

収束は、現在の基準と前の基準の対数比が閾値`thresh`未満であるときに決定されます。
