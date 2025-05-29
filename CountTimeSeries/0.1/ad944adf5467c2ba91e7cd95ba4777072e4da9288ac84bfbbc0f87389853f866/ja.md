```
INGARCHResults(y, θ, pars, λ, residuals,
      LL, LLs, nPar, nObs, se, CI, Σ,
      model, converged, MLEControl)
```

推定結果の構造。

  * `y`: 時系列
  * `θ`: 推定値（ベクトル）
  * `pars`: 推定値（パラメータ）
  * `λ`: 条件付き平均
  * `residuals`: 残差（y - λ）
  * `LL`: 尤度の最大値
  * `LLs`: 尤度の寄与
  * `nPar`: パラメータの数
  * `nObs`: 観測の数
  * `se`: 標準誤差
  * `CI`: 信頼区間
  * `Σ`: 推定量の共分散行列
  * `model`: モデルの仕様
  * `converged`: 指標、最適化ルーチンの収束？
  * `MLEControl`: 使用された推定設定
