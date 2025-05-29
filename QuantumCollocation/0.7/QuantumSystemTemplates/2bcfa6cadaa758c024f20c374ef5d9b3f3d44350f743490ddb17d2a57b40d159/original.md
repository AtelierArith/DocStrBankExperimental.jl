```
MultiTransmonSystem(
    ωs::AbstractVector{Float64},
    δs::AbstractVector{Float64},
    gs::AbstractMatrix{Float64};
    levels_per_transmon::Int = 3,
    subsystem_levels::AbstractVector{Int} = fill(levels_per_transmon, length(ωs)),
    lab_frame=false,
    subsystems::AbstractVector{Int} = 1:length(ωs),
    subsystem_drive_indices::AbstractVector{Int} = 1:length(ωs),
    kwargs...
) -> CompositeQuantumSystem
```

Returns a `CompositeQuantumSystem` object for a multi-transmon system.
