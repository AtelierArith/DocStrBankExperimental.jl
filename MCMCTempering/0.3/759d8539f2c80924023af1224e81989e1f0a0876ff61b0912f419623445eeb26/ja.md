```
RandomSwap <: AbstractSwapStrategy
```

この戦略は、すべてのチェーンインデックスをランダムにシャッフルして、`floor(numptemps(sampler)/2)` ペアのランダムな（必ずしも隣接しているわけではない）チェーンインデックスを生成し、スワップを試みます。
