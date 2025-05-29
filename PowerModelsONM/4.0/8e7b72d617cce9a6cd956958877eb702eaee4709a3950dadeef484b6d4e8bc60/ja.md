```
constraint_energized_loads_strictly_increasing(pm::AbstractUnbalancedPowerModel, n_1::Int, n_2::Int)
```

タイムステップから別のタイムステップへのエネルギー供給されている負荷ブロックの数が厳密に増加することを保証し、一度エネルギー供給されると、後のタイムステップで負荷ブロックを削減することができないという制約。
