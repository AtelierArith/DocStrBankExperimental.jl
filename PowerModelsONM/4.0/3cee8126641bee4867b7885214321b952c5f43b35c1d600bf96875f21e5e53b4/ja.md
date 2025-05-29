```
constraint_energized_blocks_strictly_increasing(pm::AbstractUnbalancedPowerModel, n_1::Int, n_2::Int)
```

ある時点から別の時点へのエネルギー供給されている負荷ブロックの数が厳密に増加し、一度エネルギー供給されると、後の時点で負荷ブロックを削減できないことを保証する制約。
