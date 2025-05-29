```
ConfidenceBands(DM::DataModel, sol::AbstractODESolution, Xdomain::HyperCube; N::Int=300, plot::Bool=isloaded(:Plots)) -> Matrix
```

Given a confidence interval `sol`, the pointwise confidence band around the model prediction is computed for x values in `Xdomain` by evaluating the model on the boundary of the confidence region.
