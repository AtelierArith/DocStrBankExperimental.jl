```
SigmaSignificance(; factor = 3.0, tail = :both) <: Significance
```

有意性テストのための構成構造体 [`significant_transitions`](@ref)。[`ChangesResults`](@ref) と一緒に使用されるとき、有意性は値が平均値 (`μ`) をどれだけ標準偏差 (`σ`) を超えているかを比較することによって推定されます。値が (もし `tail = :right` の場合) `μ + factor*σ` を超えるか、または (もし `tail = :left` の場合) `μ - factor*σ` を下回る場合、有意と見なされます。`tail = :both` の場合は、いずれかの条件がチェックされます。

`factor` は値のベクトルでもあり、その場合は各変化メトリックに対して異なる値が使用されます。

さらに [`QuantileSignificance`](@ref) を参照してください。
