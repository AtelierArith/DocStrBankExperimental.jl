```julia
function isLinear(𝒀::Union{FDobjectsVector, TFobjectsVector})
```

Return true if all objects in `𝒀` are linear. By definition, [Spectra](@ref) and [TFAmplitude](@ref) objects are linear. [CrossSpectra](@ref), [Coherence](@ref), [TFAnalyticSignal](@ref) and [TFPhase](@ref) objects may be linear or non-linear.

**See**:[FDobjectsVector](@ref), [TFobjectsVector](@ref).
