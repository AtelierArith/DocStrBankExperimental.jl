```
anova(::Type{LRT}, <model>; kwargs...)
anova(::Type{LRT}, <models>...; kwargs...)
```

Analysis of Variance by likelihood-ratio test.

Return `AnovaResult{M, LRT, N}`. See [`AnovaResult`](@ref) for details.
