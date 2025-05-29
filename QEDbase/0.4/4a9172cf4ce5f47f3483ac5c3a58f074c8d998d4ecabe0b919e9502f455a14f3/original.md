```
in_phase_space_layout(out_psl::AbstractOutPhaseSpaceLayout)::AbstractInPhaseSpaceLayout
```

This function needs to be implemented for the [`AbstractOutPhaseSpaceLayout`](@ref) interface. Given an outgoing phase space layout (`out_psl`), this function returns the associated incoming phase space layout.

This is useful for ensuring consistency between the incoming and outgoing particle momenta when calculating or sampling phase space points in scattering processes.

## Arguments

  * `out_psl`: The outgoing phase space layout, a subtype of [`AbstractOutPhaseSpaceLayout`](@ref).

## Returns

  * The associated incoming phase space layout, a subtype of [`AbstractInPhaseSpaceLayout`](@ref).
