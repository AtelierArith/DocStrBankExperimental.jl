```
LatinHypercubeSample(rng::AbstractRNG = Random.GLOBAL_RNG) <: RandomSamplingAlgorithm
```

ラテンハイパーキューブは、すべての1次元区間 `(i/n, i+1/n)` に正確に1つの点が含まれるという特性を持つ点の集合です。これは高次元空間をサンプリングするための良い方法であり、ランダムサンプルよりも均一性が高いですが、完全なネットワークほど多くの点を必要としません。
