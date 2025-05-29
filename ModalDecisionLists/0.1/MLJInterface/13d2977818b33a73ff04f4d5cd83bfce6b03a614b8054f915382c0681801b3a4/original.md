```
    ExtendedSequentialCovering
```

A model type for constructing a sequential covering classifier, based on ModalDecisionLists.jl, and implementing the MLJ model interface.

Do `model = ExtendedSequentialCovering()` to contruct an instance with default hyper-parameters. Provide keyword arguments to override hyper-parameter defaults, as in `ExtendedSequentialCovering(searchmethod=...)`

## Training data

In MLJ or MLJBase, bind an instance model to data with

`mach = machine(model, X, y)`

where

  * X: ant table of input feature (eg, a DataFrame); TODO continue here....
  * y: the target, which can be any AbstractVector whose element scitype is <:MultiClass; check the scitype with scitype(y)

Train the machine with  fit!(mach, rows=...).

## Hyperparameters

  * `searchmethod::SearchMethod=BeamSearch()`: The search method for finding single rules (see [`SearchMethod`](@ref)).
  * `max_rulebase_length::Union{Nothing,Integer}=nothing` is the maximum length of the rulebase.
  * `min_rule_coverage::Integer=1`: constrains the minimum number of instances covered by each rule.
  * `suppress_parity_warning::Bool=false`: if `true`, suppresses parity warnings.

## Fitted Parameters

The fileds of fitted_params(mach) are:

  * `fitresult`: A `DecisionList` object.

## Operations

  * `predict(mach, Xnew)`: Return a vector of predictions for each row of Xnew.

See also [`SearchMethod`](@ref),
