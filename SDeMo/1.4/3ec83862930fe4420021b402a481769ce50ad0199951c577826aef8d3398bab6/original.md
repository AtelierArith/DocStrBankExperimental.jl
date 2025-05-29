```
variables!(model::AbstractSDM, ::Type{T}, folds::Vector{Tuple{Vector{Int}, Vector{Int}}}; included=Int[], optimality=mcc, verbose::Bool=false, bagfeatures::Bool=false, kwargs...) where {T <: VariableSelectionStrategy}
```

Performs variable selection based on a selection strategy, with a possible `folds` for cross-validation. If omitted, this defaults to k-folds.

The model is retrained on the optimal set of variables after training.

**Keywords**:

  * `included` (`Int[]`), a list of variables that must be included in the model
  * `optimality` (`mcc`), the measure to optimise at each round of variable selection
  * `verbose` (`false`), whether the performance should be returned after each round of variable selection
  * `bagfeatures` (`false`), whether `bagfeatures!` should be called on each model in an homogeneous ensemble
  * all other keywords are passed to `train!` and `crossvalidate`

**Important notes**:

1. When using `bagfeatures` with a pool of included variables, they will always be present in the overall model, but not necessarilly in each model of the ensemble
2. When using `VarianceInflationFactor`, the variable selection will stop even if the VIF is above the threshold, if it means producing a model with a lower performance – using `variables!` will *always* lead to a better model
