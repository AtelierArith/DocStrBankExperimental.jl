```
build_laplace_objective(build_latent_gp, xs, ys; kwargs...)
```

ラプラス近似における潜在GPのハイパーパラメータを最適化するための最小化目的を計算するクロージャを構築します。返されるクロージャはその引数を`build_latent_gp`に渡し、`LatentGP`の事前分布を返さなければなりません。

# キーワード引数

  * `newton_warmstart=true`: (デフォルト) 前回の目的関数呼び出しのモードでニュートン最適化を開始します
  * `newton_callback`: 各ニュートンステップの後に`newton_callback(fnew, cache)`として呼び出されます
  * `newton_maxiter=100`: ニュートンステップの最大数。
