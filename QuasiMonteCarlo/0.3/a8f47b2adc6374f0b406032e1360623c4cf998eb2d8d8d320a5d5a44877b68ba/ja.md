```julia
DesignMatrix(n, d, sample_method::DeterministicSamplingAlgorithm, num_mats, T = Float64)
```

i.i.d. ランダム化を QMC シーケンスに対して複数回行うためのイテレータを作成します。ここで

  * `num_mats` はイテレータの長さです。
  * `n` はサンプリングするポイントの数です。
  * `d` は点集合の次元であり、`[0, 1)ᵈ` にあります。
  * `sample_method` は決定論的な点集合 `out` を作成するために使用される準モンテカルロサンプリング戦略です。
  * `T` は点集合の `eltype` です。一部の QMC メソッド（Faure、Sobol）では、これを `Rational` にすることができます。

これはすべてのスクランブリングメソッドおよびシフトと互換性があります。また、`Distributions.Sampleable` または `RandomSample` とともに使用することもできます。
