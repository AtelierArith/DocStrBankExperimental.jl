```
ThresholdSignificance(threshold::Real; tail = :right) <: Significance
```

[`significant_transitions`](@ref)における有意性検定のための構成体です。有意性は、各変化メトリックの値を指定された`threshold`と比較することによって推定されます。閾値を超える値（`tail = :right`の場合）または閾値を下回る値（`tail = :left`の場合）は、有意と見なされます。`tail = :both`の場合は、いずれの条件もチェックされます。
