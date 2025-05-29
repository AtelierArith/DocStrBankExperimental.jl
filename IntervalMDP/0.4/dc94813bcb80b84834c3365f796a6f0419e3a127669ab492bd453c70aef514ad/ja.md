```
reach(prop::FiniteTimeReachability)
```

有限時間到達性プロパティの到達可能性を計算するための状態の集合を返します。これは、通常の到達性プロパティに対する [`terminal_states(prop::FiniteTimeReachability)`](@ref) と同等です。到達性と終端状態が異なるより複雑なプロパティについては、[`FiniteTimeReachAvoid`](@ref) を参照してください。
