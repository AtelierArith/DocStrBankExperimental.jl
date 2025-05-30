```
QuantileSignificance(; p = 0.95, tail = :both) <: Significance
```

有意性テストのための構成体 [`significant_transitions`](@ref)。[`ChangesResults`](@ref) と一緒に使用されると、各変化指標の値がその `p`-分位数と比較されることによって有意性が推定されます。`tail = :right` の場合は `p`-分位数を超える値、`tail = :left` の場合は `1-p`-分位数を下回る値が有意と見なされます。`tail = :both` の場合は、いずれかの条件がチェックされます。

`QuantileSignficance` は、分位数の定義によっていくつかの値が有意であることを保証します。類似の [`SigmaSignificance`](@ref) も参照してくださいが、こちらはこの保証がありません。
