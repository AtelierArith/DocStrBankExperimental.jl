```
OptimizationMAP(; kwargs...)
```

モデルのパラメータとハイパーパラメータのMAP推定をOptimization.jlパッケージを使用して見つけます。

# キーワード

  * `algorithm::Any`: 最適化アルゴリズムを定義します。
  * `multistart::Union{Int, Matrix{Float64}}`: 最適化の再起動の回数、または最適化実行の初期（ハイパ）パラメータ値を含むタプルのベクトル`(θ, λ, α)`。
  * `parallel::Bool`: `parallel=true`の場合、個々の再起動が並行して実行されます。
  * `softplus_hyperparams::Bool`: `softplus_hyperparams=true`の場合、ソフトプラス関数がGPハイパーパラメータ（長さスケールと振幅）およびノイズ偏差に適用され、最適化中に正の値を確保します。
  * `softplus_params::Union{Bool, Vector{Bool}}`: ソフトプラス関数を適用して正の値を確保すべきパラメータを定義します。バイナリベクトルの代わりにブール値を供給すると、すべてのパラメータに対してソフトプラスがオン/オフになります。デフォルトは`false`で、ソフトプラスはパラメータには適用されません。
