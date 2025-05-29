```
smooth(x, λ, f, ∇f!, y_prev)
```

一般的な滑らかな関数 `f` の近接演算子を、インプレース勾配 `∇f!` とスケーリングパラメータ `λ` を用いて `x` で計算します。ウォームスタートは、前の解である `y_prev` を使用することで対応しています。

#### 引数

  * `x::AbstractVector`     : 入力
  * `λ::Real`               : スケーリングパラメータ
  * `f::Function`           : 目的関数
  * `∇f!::Function`         : 勾配
  * `y_prev::AbstractVector`: 前の出力

#### 戻り値

  * `y::AbstractVector` : 出力

```
