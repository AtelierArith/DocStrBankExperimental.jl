```
ParameterAggregator(parfullnames::Vector{String}, model; eltype=Float64) -> ParameterAggregator
```

Represent a subset of model parameters given by `parfullnames` as a flattened Vector

`parfulnames` is a Vector of form `["domainname.reactionname.parname", ...]` defining a subset of model parameters (NB: must be of type `ParDouble` or `ParDoubleVec` ie scalar or vector of Float64).

`norm_values` can be used to specify normalisation of the flattened parameter vector (defaults to 1.0).

The parameters can then be set from and copied to a flattened Vector using:

```
copyto!(pa::ParameterAggregator, newvalues::Vector)  # set from newvalues .* norm_values
copyto!(currentvalues::Vector, pa::ParameterAggregator) # copy to currentvalues, dividing by norm_values
get_currentvalues(pa::ParameterAggregator) -> currentvalues::Vector
```

The subset of parameters are then defined by the `p` parameter Vector used by SciML solvers, and  combined with the full set (from the yaml file) to eg solve an ODE to enable sensitivity studies.

`eltype` can be eg a Dual number to support ForwardDiff automatic differentiation for parameter Jacobians.
