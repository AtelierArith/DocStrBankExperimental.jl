```
JuMP.owner_model(cref::InfOptConstraintRef)::InfiniteModel
```

Extend `JuMP.owner_model` to return the infinite model associated with `cref`.

**Example**

```julia-repl
julia> model = owner_model(cref)
An InfiniteOpt Model
Minimization problem with:
Finite Parameters: 0
Infinite Parameters: 3
Variables: 3
Derivatives: 0
Measures: 0
Objective function type: GeneralVariableRef
`GenericAffExpr{Float64,GeneralVariableRef}`-in-`MathOptInterface.EqualTo{Float64}`: 1 constraint
Names registered in the model: g, t, h, x
Optimizer model backend information:
Model mode: AUTOMATIC
CachingOptimizer state: NO_OPTIMIZER
Solver name: No optimizer attached.
```
