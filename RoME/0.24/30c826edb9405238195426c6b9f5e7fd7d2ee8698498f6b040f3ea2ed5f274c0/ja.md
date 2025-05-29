```julia
enableSolveAllNotDRT!(dfg; solvable)

```

すべての周辺化を削除し、ラベルに `drt` を含まないすべての変数と要因を solvable (=1) にします。

ノート

  * デッドレッキングテザー (DRT)

開発ノート

  * レガシー、実装が不十分で、改善が必要

関連

dontMarginalizeVariablesAll!, setSolvable!, defaultFixedLagOnTree!
