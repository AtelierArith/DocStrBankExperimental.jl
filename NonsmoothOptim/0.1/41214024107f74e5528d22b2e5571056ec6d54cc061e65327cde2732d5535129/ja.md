```
abstract type ConstrainedNonSmoothProblem <: NonSmoothProblem
```

制約付き非滑らか最適化問題を表します。これは `NonSmoothProblem` に関して新しい特性を暗示するものではありません。なぜなら、それらは使用される最適化ソルバーの種類（指標関数、ポリトープ、射影演算子、近接演算子など）に大きく依存する可能性があるからです。
