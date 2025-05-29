```
requires_disaggregation(vref::JuMP.AbstractVariableRef)::Bool
```

Return a `Bool` whether `vref` requires disaggregation for the [`Hull`](@ref)  reformulation. This is intended as an extension point for interfaces with  DisjunctiveProgramming that use variable reference types that are not  `JuMP.GenericVariableRef`s. Errors if `vref` is not a `JuMP.GenericVariableRef`. See also [`make_disaggregated_variable`](@ref).
