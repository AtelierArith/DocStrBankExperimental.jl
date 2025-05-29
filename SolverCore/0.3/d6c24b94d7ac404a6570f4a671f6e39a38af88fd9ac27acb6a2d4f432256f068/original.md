```
reset!(stats::GenericExecutionStats)
reset!(stats::GenericExecutionStats, nlp::AbstractNLPModel)
```

Reset the internal flags of `stats` to `false` to Indicate that the contents should not be trusted. If an `AbstractNLPModel` is also provided,  the pre-allocated vectors are adjusted to the problem size.
