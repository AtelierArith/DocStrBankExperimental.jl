```
r = AdaptiveMetropolis(x0; kwargs)
r = AdaptiveMetropolis(x0, [scale, [step]])
```

AdaptiveMetropolis状態のコンストラクタ。

# 引数

  * `x0`: 初期状態ベクトル

# キーワード引数

  * `scale`: スケーリングパラメータ; デフォルトは `2.38/sqrt(d)` で、ここで `d` は次元。
  * `step`: ステップサイズオブジェクト; デフォルトは `PolynomialStepSize(1.0)`
  * `S_init`: 初期提案形状のコレスキー因子; デフォルトは `identity_cholesky(x0)`

`s` が `RWMState` の場合、提案サンプルは `draw!(s, r)` を呼び出すことで引き出され、適応は `adapt!(r, s)` または `adapt_rb!(r, s, α)` で行われます。
