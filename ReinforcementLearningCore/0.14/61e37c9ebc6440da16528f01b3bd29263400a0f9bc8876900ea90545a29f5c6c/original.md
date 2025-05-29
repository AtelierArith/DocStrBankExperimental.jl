```
RLBase.plan!(s::EpsilonGreedyExplorer, values; step) where T
```

!!! note
    If multiple values with the same maximum value are found. Then a random one will be returned when `is_break_tie==true`.

    `NaN` will be filtered unless all the values are `NaN`. In that case, a random one will be returned.

