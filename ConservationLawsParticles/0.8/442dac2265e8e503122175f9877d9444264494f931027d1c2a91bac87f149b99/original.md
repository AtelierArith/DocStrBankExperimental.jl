```
compute_interaction(t, x, interaction, ys[, dens_diff])
```

Evaluates the interaction generated by the particles `ys` at `(t, x)`.

`interaction` can be a `SampledInteraction`, an `IntegratedInteraction`, or any other form of interaction that provides this interface.

See also [`SampledInteraction`](@ref), [`IntegratedInteraction`](@ref), [`sampled_interaction`](@ref), [`integrated_interaction`](@ref).
