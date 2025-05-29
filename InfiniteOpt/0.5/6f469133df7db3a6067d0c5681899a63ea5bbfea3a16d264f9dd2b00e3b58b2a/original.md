```
JuMP.optimizer_index(cref::InfOptConstraintRef; 
                     [label::Type{<:AbstractSupportLabel} = PublicLabel,
                     ndarray::Bool = false, kwargs...])
```

Extend `JuMP.optimizer_index` to return the `MathOptInterface` index(es) of  `cref` in accordance with its reformulation constraints(s) stored in the  optimizer model. 

The keyword arugments `label` and `ndarray` are what `TranscriptionOpt` employ  and `kwargs` denote extra ones that user extensions may employ.

By default only the optimizer indices associated with public supports are returned, the  full set can be accessed via `label = All`. Moreover, the indices of infinite  constraints are returned as a list. However, a n-dimensional array  can be obtained via `ndarray = true` which is handy when the constraint has multiple  infinite parameter dependencies.

It may also be helpful to query via [`optimizer_model_constraint`](@ref) to retrieve the constraints(s) that these indices are based on. The same keyword  arguments should be used for consistency.

For extensions, this only works if [`optimizer_model_constraint`](@ref) has been extended correctly and/or [`map_optimizer_index`](@ref) has been extended for constraints.

**Example**

```julia-repl
julia> optimizer_index(c1)
4-element Array{MathOptInterface.ConstraintIndex{MathOptInterface.ScalarAffineFunction{Float64},MathOptInterface.GreaterThan{Float64}},1}:
 MathOptInterface.ConstraintIndex{MathOptInterface.ScalarAffineFunction{Float64},MathOptInterface.GreaterThan{Float64}}(1)
 MathOptInterface.ConstraintIndex{MathOptInterface.ScalarAffineFunction{Float64},MathOptInterface.GreaterThan{Float64}}(2)
 MathOptInterface.ConstraintIndex{MathOptInterface.ScalarAffineFunction{Float64},MathOptInterface.GreaterThan{Float64}}(3)
 MathOptInterface.ConstraintIndex{MathOptInterface.ScalarAffineFunction{Float64},MathOptInterface.GreaterThan{Float64}}(4)
```
