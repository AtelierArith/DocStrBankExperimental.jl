```
compute_extreme_point(lmo::LinearMinimizationOracle, direction; kwargs...)
```

点 `argmin_{v ∈ C} v ⋅ direction` を計算します。ここで、`C` は LMO によって表される集合です。ほとんどの LMO では、`v` がキーワード引数として特徴付けられており、`v` が密である場合にはインプレース計算を可能にします。すべての LMO は無視できるキーワード引数を受け入れるべきです。
