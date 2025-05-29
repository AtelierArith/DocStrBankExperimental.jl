```
fista!(X::AbstractArray{Float64,2}, Y::AbstractArray{Float64,2}, 
            Z::AbstractArray{Float64,2}, 
            lambda::Float64, alpha::Float64,
            B::AbstractArray{Float64,2}, 
            regXidx::AbstractArray{Int64,1}, 
            regZidx::AbstractArray{Int64,1}, reg::BitArray{2}, norms; 
            isVerbose::Bool=true, stepsize::Float64=0.01, 
            thresh::Float64=10.0^(-7), maxiter::Int=10^10)
```

固定ステップサイズでElastic-netバージョンのFISTAを実行します。

# 引数

  * X = 行の共変量からなる浮動小数点の2次元配列で、すべてのカテゴリ変数が適切なコントラストでコーディングされています
  * Y = 多変量応答からなる浮動小数点の2次元配列
  * Z = 列の共変量からなる浮動小数点の2次元配列で、すべてのカテゴリ変数が適切なコントラストでコーディングされています
  * lambda = ペナルティパラメータ、浮動小数点スカラー
  * alpha = L1とL2のペナルティの混合を決定するパラメータ (ϵ[0, 1])
  * B = 開始係数推定からなる浮動小数点の2次元配列
  * regXidx = 正則化されたX共変量に対応するインデックスの1次元配列
  * regZidx = 正則化されたZ共変量に対応するインデックスの1次元配列
  * reg = 各係数を正則化するかどうかを示すビットの2次元配列
  * norms = 各係数に対応するノルムからなる浮動小数点の2次元配列または`nothing`

# キーワード引数

  * isVerbose = メッセージを印刷するかどうかを示すブールフラグ。デフォルトは`true`。
  * stepsize = 浮動小数点; 更新のためのステップサイズ。デフォルトは`0.01`。
  * thresh = 係数が収束したと見なされる閾値、浮動小数点スカラー。デフォルトは`10^(-7)`。
  * maxiter = 更新反復の最大数。デフォルトは`10^10`。

# 値

なし; 係数をその場で更新します

# 一部の注意事項

収束は、現在の基準と前の基準の対数比が閾値`thresh`未満であるときに決定されます。

`fista!`の固定ステップサイズを選択するためのデフォルトの方法は、`X*transpose(X)`と`Z*transpose(Z)`の最大固有値の積の逆数を使用することです。これは、`fista!`が`fun`引数に渡され、`setStepSize`が`true`に設定されているときに`mlmnet`関数によって計算されます。`setStepSize`が`false`に設定されている場合、`stepsize`引数の値が固定ステップサイズとして使用されます。`X`および/または`Z`が非常に大きい場合、固有値を取得することは計算上の制限を超える可能性があることに注意してください。
