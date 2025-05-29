```
SingleSwap <: AbstractSwapStrategy
```

各スワップステップで、この戦略は単一のチェインインデックス `i` をサンプリングし、チェイン `i` と `i + 1` の間でスワップを提案します。

このアプローチはいくつかの名前で知られており、例えば、パラレルテンパリング (PT) MCMC やレプリカ交換 MCMC などです。[^PTPH05]

[^PTPH05]: Earl, D. J., & Deem, M. W., Parallel tempering: theory, applications, and new perspectives, Physical Chemistry Chemical Physics, 7(23), 3910–3916 (2005).
