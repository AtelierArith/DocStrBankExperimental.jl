```julia
DesignMatrix(n, d, sample_method::DeterministicSamplingAlgorithm, num_mats, T = Float64)
```

i.i.d. ランダム化を QMC シーケンスに対して複数回行うためのイテレータを作成します。ここで

  * `num_mats` はイテレータの長さです。
  * `n` はサンプリングするポイントの数です。
  * `d` は `[0, 1)ᵈ` 内のポイントセットの次元数です。
  * `sample_method` は決定論的なポイントセット `out` を作成するために使用される準モンテカルロサンプリング戦略です。
  * `T` はポイントセットの `eltype` です。一部の QMC メソッド（Faure、Sobol）では、これを `Rational` にすることができます。

これはすべてのスクランブリング方法およびシフトと互換性があります。また、`Distributions.Sampleable` または `RandomSample` と一緒に使用することもできます。
