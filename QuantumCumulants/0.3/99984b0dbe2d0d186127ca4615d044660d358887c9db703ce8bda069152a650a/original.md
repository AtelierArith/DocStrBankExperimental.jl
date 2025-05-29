```
evaluate(eqs::IndexedMeanfieldEquations;limits)
evaluate(corr::CorrelationFunction;limits)
evaluate(x;limits)
```

Function, that evaluates a given [`MeanfieldEquations`](@ref) entity and returns again equations, where indices have been inserted and sums evaluated. Can also be called on individual terms and a [`CorrelationFunction`](@ref) entity, to evaluate any summations inside these terms.

# Arguments

*`me::MeanfieldEquations`: A [`MeanfieldEquations`](@ref) entity, which shall be evaluated.

# Optional argumentes

*`limits::Dict{BasicSymbolic,Int64}=Dict{Symbol,Int64}()`: A seperate dictionary, to     specify any symbolic limits used when [`Index`](@ref) entities were defined. This needs     to be specified, when the equations contain summations, for which the upper bound is given     by a Symbolic. *`h`: A HilbertSpace, Vector of Hilbertspaces or Numbers, specifying the specific Hilbertspaces,     that shall be evaluated. Does not evaluate any other Hilbertspace, other than the given ones.
