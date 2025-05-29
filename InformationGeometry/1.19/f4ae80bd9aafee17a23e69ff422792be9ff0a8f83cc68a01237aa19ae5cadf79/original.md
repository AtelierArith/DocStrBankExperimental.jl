```
GenerateInterruptedBoundary(DM::AbstractDataModel, u0::AbstractVector{<:Number}; Boundaries::Union{Function,Nothing}=nothing, tol::Real=1e-9,
                            redo::Bool=true, meth::AbstractODEAlgorithm=Tsit5(), mfd::Bool=true, ADmode::Val=Val(:ForwardDiff), kwargs...) -> ODESolution
```

Integrates along the level lines of the log-likelihood in the counter-clockwise direction until the model becomes either

1. structurally non-identifiable via `det(g) < tol`
2. the given `Boundaries(u,t,int)` method evaluates to `true`.

It then integrates from where this obstruction was met in the clockwise direction until said obstruction is hit again, resulting in a half-open confidence region.
