```
JuMP.owner_model(vref::GeneralVariableRef)::InfiniteModel
```

Extend `JuMP.owner_model` to return the model where `vref` is stored.

**Example**

```julia-repl
julia> owner_model(vref)
An InfiniteOpt Model
Feasibility problem with:
Finite Parameters: 0
Infinite Parameters: 0
Variable: 1
Derivatives: 0
Measures: 0
`FiniteVariableRef`-in-`MathOptInterface.GreaterThan{Float64}`: 1 constraint
`FiniteVariableRef`-in-`MathOptInterface.LessThan{Float64}`: 1 constraint
Names registered in the model: vref
Optimizer model backend information:
Model mode: AUTOMATIC
CachingOptimizer state: NO_OPTIMIZER
Solver name: No optimizer attached.
```
