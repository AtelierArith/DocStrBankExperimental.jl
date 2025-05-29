```julia
struct TVLogistic <: TransformVariables.ScalarTransform
```

ロジスティック変換 `x ↦ logit(x)`。すべての実数から (0, 1) へのマッピング。
