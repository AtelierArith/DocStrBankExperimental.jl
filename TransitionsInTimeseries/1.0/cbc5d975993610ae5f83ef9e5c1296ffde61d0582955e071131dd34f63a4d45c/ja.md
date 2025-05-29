```
ChangesConfig
```

時系列における「変化」が[`estimate_changes`](@ref)でどのように推定されるかのスーパークラス。「変化」は[`significant_transitions`](@ref)で統計的に有意と見なされるものであり、時系列における「遷移」です。

`ChangesConfig`の既存のサブタイプは次のとおりです：

  * [`SlidingWindowConfig`](@ref).
  * [`SegmentedWindowConfig`](@ref).
  * [`SlopeChangeConfig`](@ref).
