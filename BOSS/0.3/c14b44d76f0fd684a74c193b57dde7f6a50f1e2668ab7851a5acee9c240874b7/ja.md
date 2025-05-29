```
SampleOptMAP(; kwargs...)
SampleOptMAP(::SamplingMAP, ::OptimizationMAP)
```

`SamplingMAP`と`OptimizationMAP`を組み合わせて、最初に事前分布から多くのパラメータサンプルをサンプリングし、その後、最良のサンプルから初期化された複数の最適化実行を開始します。

# キーワード

  * `samples::Int`: 引かれたサンプルの数。
  * `algorithm::Any`: 最適化アルゴリズムを定義します。
  * `multistart::Int`: 最適化の再起動の数。
  * `parallel::Bool`: `parallel=true`の場合、サンプリングと最適化の両方が並行して実行されます。
  * `softplus_hyperparams::Bool`: `softplus_hyperparams=true`の場合、ソフトプラス関数がGPハイパーパラメータ（長さスケールと振幅）およびノイズ偏差に適用され、最適化中に正の値を確保します。
  * `softplus_params::Union{Bool, Vector{Bool}}`: ソフトプラス関数を適用して正の値を確保すべきパラメトリックモデルのどのパラメータに適用するかを定義します。バイナリベクトルの代わりにブール値を供給すると、すべてのパラメータに対してソフトプラスがオン/オフになります。デフォルトは`false`で、ソフトプラスはパラメータには適用されません。
