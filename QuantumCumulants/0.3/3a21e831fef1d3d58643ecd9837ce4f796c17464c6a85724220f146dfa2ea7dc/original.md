```
evalME(me::MeanfieldEquations;limits::Dict{SymbolicUtils.BasicSymbolic,Int64}=Dict{SymbolicUtils.BasicSymbolic,Int64}())
```

Function, that evaluates a given [`MeanfieldEquations`](@ref) entity and returns again equations, where indices have been inserted and sums evaluated.

# Arguments

*`me::MeanfieldEquations`: A [`MeanfieldEquations`](@ref) entity, which shall be evaluated.

# Optional argumentes

*`limits=Dict{SymbolicUtils.BasicSymbolic,Int64}()`: A seperate dictionary, to     specify any symbolic limits used when [`Index`](@ref) entities were defined. This needs     to be specified, when the equations contain summations, for which the upper bound is given     by a Symbolic.
