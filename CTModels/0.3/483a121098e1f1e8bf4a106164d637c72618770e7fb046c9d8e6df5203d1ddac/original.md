```julia
constraint(
    model::CTModels.Model,
    label::Symbol
) -> Tuple{Symbol, Any, Any, Any}

```

Get a labelled constraint from the model. Returns a tuple of the form `(type, f, lb, ub)` where `type` is the type of the constraint, `f` is the function of the constraint, `lb` is the lower bound of the constraint and `ub` is the upper bound of the constraint. 

The function returns an exception if the label is not found in the model.
