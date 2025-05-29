```
evaluate(reg::AbstractRegularizer, skymodel::AbstractImageModel, x::AbstractArray)
```

与えられた画像モデルの与えられた画像パラメータに対する正則化関数の値を計算します。デフォルトでは、evaluate(domain(reg), reg, skymodel, x)を返します。

# 引数

  * `reg::AbstractRegularizer`: 正則化関数。
  * `skymodel::AbstractImageModel`: 入力画像のモデル
  * `x::AbstractArray`: 入力画像のパラメータ
