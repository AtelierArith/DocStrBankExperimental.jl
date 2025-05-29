```
RLBase.plan!(s::EpsilonGreedyExplorer, values; step) where T
```

!!! note
    同じ最大値を持つ複数の値が見つかった場合、`is_break_tie==true` のときにランダムなものが返されます。

    すべての値が `NaN` でない限り、`NaN` はフィルタリングされます。その場合、ランダムなものが返されます。

