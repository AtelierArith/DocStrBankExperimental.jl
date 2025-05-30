```
GridSample(R::RandomizationMethod = NoRand()) <: DeterministicSamplingAlgorithm
```

単純な長方形グリッド格子。`dx = (ub - lb)/n` のグリッドから `n` 個のランダムサンプルをサンプリングします。

2次元を超えると、グリッドは単純モンテカルロよりも悪い不一致を持ちます。その結果、マルチバリアント積分にはほとんど使用されるべきではなく、他のアルゴリズムの出発点としての使用が推奨されます。
