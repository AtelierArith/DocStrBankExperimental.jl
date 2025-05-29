```
OptimizationFunction(nlpmodel::AbstractNLPModel, adtype::AbstractADType = NoAD())
```

Returns an `OptimizationFunction` from the `NLPModel` defined in `nlpmodel` where the available derivates are re-used from the model, and the rest are populated with the Automatic Differentiation backend specified by `adtype`.
