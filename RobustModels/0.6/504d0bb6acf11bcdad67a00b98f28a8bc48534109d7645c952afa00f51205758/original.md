```
RobustLinearModel
```

Robust linear model representation

## Fields

  * `resp`: the [`RobustLinResp`](@ref) structure.
  * `pred`: the predictor structure, of type [`DensePredChol`](@ref), [`SparsePredChol`](@ref), [`DensePredCG`](@ref), [`SparsePredCG`](@ref) or [`RidgePred`](@ref).
  * `formula`: either a `FormulaTerm` object or `nothing`
  * `fitdispersion`: if true, the dispersion is estimated otherwise it is kept fixed
  * `fitted`: if true, the model was already fitted
