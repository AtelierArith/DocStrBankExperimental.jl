```
model, nls_model, sol = random_matrix_completion_model(; kwargs...)
```

`NLPModel`のインスタンスと、同じ行列補完問題を表す`NLSModel`のインスタンスを返します。すなわち、平方線形最小二乗目的

½ ‖P(X - A)‖²

フロベニウスノルムにおいて、Xはm x n行列として表される未知の画像、Aは固定された画像であり、演算子PはXとAの特定のピクセルのサブセットのみを保持します。

## キーワード引数

  * `m :: Int`: XとAの行数 (デフォルト: 100)
  * `n :: Int`: XとAの列数 (デフォルト: 100)
  * `r :: Int`: Aの希望するランク (デフォルト: 5)
  * `sr :: AbstractFloat`: ピクセルのセットを決定するために使用される0から1の間の閾値

演算子Pによって保持される (デフォルト: 0.8)

  * `va :: AbstractFloat`: Aに適用される最初のガウス摂動の分散 (デフォルト: 1.0e-4)
  * `vb :: AbstractFloat`: Aに適用される2番目のガウス摂動の分散 (デフォルト: 1.0e-2)
  * `c :: AbstractFloat`: 2つのガウス摂動の凸結合の係数 (デフォルト: 0.2)。

## 戻り値

同じ行列補完問題を表す`FirstOrderModel`と`FirstOrderNLSModel`のインスタンス、および正確な解を返します。
