```
ComposedStopCondition(stop_conditions...; reducer = any)
```

The result of `stop_conditions` is reduced by `reducer`. The default `reducer` is the `any` function, which means that the condition is true when any one of the `stop_conditions...` is true. Can be replaced by any function returning a boolean. For example `reducer = x->sum(x) >= 2` will require at least two of the conditions to be true.
