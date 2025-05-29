```
abstract type SingleManifoldAlgorithm{M <: Manifold} <: Algorithm{M}
```

単一多様体アルゴリズムの抽象スーパタイプ、すなわち、単一の多様体でのみ動作することが知られているアルゴリズムです。

多様体は `manifold(alg)` を介してアクセスできます。
