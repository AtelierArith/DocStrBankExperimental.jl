```
AutoCorrelationLogger(observable::Function, TA::DataType,
                        observable_length::Integer, n_correlation::Integer)
```

自己相関ロガーであり、`observableA == observableB`の場合は[`TimeCorrelationLogger`](@ref)に相当します。
