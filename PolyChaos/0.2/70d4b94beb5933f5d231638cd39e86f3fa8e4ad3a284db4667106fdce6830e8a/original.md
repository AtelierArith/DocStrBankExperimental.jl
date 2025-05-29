**Univariate**

```
samplePCE(n::Int,x::AbstractVector{<:Real},op::AbstractOrthoPoly;method::String="adaptiverejection")
```

Combines [`sampleMeasure`](@ref) and [`evaluatePCE`](@ref), i.e. it first draws `n` samples from the measure, then evaluates the PCE for those samples.

**Multivariate**

```
samplePCE(n::Int,x::AbstractVector{<:Real},mop::MultiOrthoPoly;method::Vector{String}=["adaptiverejection" for i=1:length(mop.meas.name)])
```
