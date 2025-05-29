```
fit(VS::Type{<:UnivariateVolatilitySpec}, data; dist=StdNormal, meanspec=Intercept,
    algorithm=BFGS(), autodiff=:forward, kwargs...)
```

`VS`で指定されたARCHモデルを`data`にフィットさせます。`data`はベクトルまたはGLM.LinearModel（またはGLM.TableRegressionModel）であることができます。

# キーワード引数:

  * `dist=StdNormal`: 誤差分布。
  * `meanspec=Intercept`: 平均仕様、タイプまたはそのタイプのインスタンスとして。
  * `algorithm=BFGS(), autodiff=:forward, kwargs...`: 最適化器に渡されます。

# 例: インターセプトなしのEGARCH{1, 1, 1}モデル、Student's t誤差。

```jldoctest
julia> fit(EGARCH{1, 1, 1}, BG96; meanspec=NoIntercept, dist=StdT)

EGARCH{1, 1, 1}モデル、Student's t誤差、T=1974。


ボラティリティパラメータ:
──────────────────────────────────────────────
      推定値  標準誤差    z値  Pr(>|z|)
──────────────────────────────────────────────
ω   -0.0162014  0.0186806  -0.867286    0.3858
γ₁  -0.0378454  0.018024   -2.09972     0.0358
β₁   0.977687   0.012558   77.8538      <1e-99
α₁   0.255804   0.0625497   4.08961     <1e-04
──────────────────────────────────────────────

分布パラメータ:
─────────────────────────────────────────
   推定値  標準誤差  z値  Pr(>|z|)
─────────────────────────────────────────
ν   4.12423    0.40059  10.2954    <1e-24
─────────────────────────────────────────
```
