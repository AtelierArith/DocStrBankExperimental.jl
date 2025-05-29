```
evaluate(domain::AbstractRegularizerDomain, reg::AbstractRegularizer, skymodel::AbstractImageModel, x::AbstractArray)
```

与えられた画像モデルに対する与えられた画像パラメータの正則化関数の値を計算します。デフォルトでは、0を返します。

# 引数

  * `domain::AbstractRegularizerDomain`: 正則化関数が計算される画像のドメイン。
  * `reg::AbstractRegularizer`: 正則化関数。
  * `skymodel::AbstractImageModel`: 入力画像のモデル
  * `x::AbstractArray`: 入力画像のパラメータ
