```
OptimizationProblem(nlpmodel::AbstractNLPModel, adtype::AbstractADType = NoAD())
```

Returns an `OptimizationProblem` with the bounds and constraints defined in `nlpmodel`. The optimization function and its derivatives are re-used from `nlpmodel` when available or populated wit the Automatic Differentiation backend specified by `adtype`.
