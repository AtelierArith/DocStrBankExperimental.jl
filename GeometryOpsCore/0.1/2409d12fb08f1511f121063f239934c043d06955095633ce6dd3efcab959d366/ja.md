```
abstract type ManifoldIndependentAlgorithm{M <: Manifold} <: Algorithm{M}
```

多様体に依存しないアルゴリズムの抽象スーパタイプ、すなわち、任意の多様体で動作する可能性のあるものです。

多様体は `ManifoldIndependentAlgorithm` のアルゴリズムに保存され、`manifold(alg)` を介してアクセスされます。
