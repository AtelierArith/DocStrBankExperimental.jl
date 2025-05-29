```
SingleRandomSwap <: AbstractSwapStrategy
```

各スワップステップで、この戦略は2つのチェーンインデックス `i` と `j` をサンプリングし、対応する2つのチェーン間でのスワップを提案します。

このアプローチは、特定のモデルに対して効果的であることが示されています [^1]。

[^1]: Malcolm Sambridge, A Parallel Tempering algorithm for probabilistic sampling and multimodal optimization, Geophysical Journal International, Volume 196, Issue 1, January 2014, Pages 357–374, https://doi.org/10.1093/gji/ggt342
