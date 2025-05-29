```
AutoCorrelationLogger(observable::Function, TA::DataType,
                        observable_length::Integer, n_correlation::Integer)
```

An autocorrelation logger, equivalent to a [`TimeCorrelationLogger`](@ref) in the case that `observableA == observableB`.
