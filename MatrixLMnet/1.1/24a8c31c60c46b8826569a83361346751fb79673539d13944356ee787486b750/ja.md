```
admm!(X::AbstractArray{Float64,2}, Y::AbstractArray{Float64,2}, 
           Z::AbstractArray{Float64,2}, lambda::Float64, alpha::Float64,
           B::AbstractArray{Float64,2}, 
           regXidx::AbstractArray{Int64,1}, 
           regZidx::AbstractArray{Int64,1}, reg::BitArray{2}, norms, 
           Qx::AbstractArray{Float64,2}, Qz::AbstractArray{Float64,2}, 
           U::AbstractArray{Float64,2}, L::AbstractArray{Float64,2}; 
           isVerbose::Bool=true, stepsize::Float64=0.01, 
           rho::Float64=1.0, setRho::Bool=true, 
           thresh::Float64=10.0^(-7), maxiter::Int=10^10, 
           tau_incr::Float64=2.0, tau_decr::Float64=2.0, mu::Float64=10.0)
```

ADMMを実行します。

# 引数

  * X = 行の共変量からなる浮動小数点の2次元配列で、すべてのカテゴリ変数が適切なコントラストでコーディングされています
  * Y = 多変量応答からなる浮動小数点の2次元配列
  * Z = 列の共変量からなる浮動小数点の2次元配列で、すべてのカテゴリ変数が適切なコントラストでコーディングされています
  * lambda = ラムダペナルティ、浮動小数点スカラー
  * alpha = L1とL2のペナルティの混合を決定するパラメータ (ϵ[0, 1])
  * B = 開始係数推定からなる浮動小数点の2次元配列
  * regXidx = 正則化されたX共変量に対応するインデックスの1次元配列
  * regZidx = 正則化されたZ共変量に対応するインデックスの1次元配列
  * reg = 各係数を正則化するかどうかを示すビットの2次元配列
  * norms = 各係数に対応するノルムからなる浮動小数点の2次元配列または`nothing`
  * Qx = Xの固有ベクトルからなる浮動小数点の2次元配列
  * Qz = Zの固有ベクトルからなる浮動小数点の2次元配列
  * U = 変換されたY行列からなる浮動小数点の2次元配列
  * L = XとZの固有値のクロネッカー積からなる浮動小数点の2次元配列

# キーワード引数

  * isVerbose = メッセージを表示するかどうかを示すブールフラグ。デフォルトは`true`。
  * stepsize = 浮動小数点; 更新のステップサイズ（ADMMには無関係）。デフォルトは`0.01`。
  * rho = 浮動小数点; ADMMの調整を制御するパラメータ。デフォルトは`1.0`。
  * setRho = ADMMの調整パラメータ`rho`を計算するかどうかを示すブールフラグ。デフォルトは`true`。
  * thresh = 係数が収束したと見なされる閾値、浮動小数点スカラー。デフォルトは`10^(-7)`。
  * maxiter = 更新反復の最大数。デフォルトは`10^10`。
  * tau_incr = 浮動小数点; rhoが増加するファクターを制御するパラメータ。デフォルトは2.0。
  * tau_decr = 浮動小数点; rhoが減少するファクターを制御するパラメータ。デフォルトは2.0。
  * mu = 浮動小数点; プライマルとデュアルの残差が互いにどの程度内側にあるべきかを制御するパラメータ。デフォルトは10.0。

# 値

なし; 係数をその場で更新します

# 一部の注意事項

収束は、現在の基準と前の基準の対数比が閾値`thresh`未満であるときに決定されます。

`rho`はADMMの調整を制御し、ユーザーによって指定できます。
