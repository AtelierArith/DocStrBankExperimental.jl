```julia
UnitCubeDomain(; kwargs...)

```

Creates a unit-sized 3D cube domain spanning from `0.0` to `1.0` in each dimension.

# Keyword Arguments

  * `periodic_dims`: List of periodic dimensions in `1:D`. Defaults to none.
  * `tag`: Domain tag (symbol) defaults to `:Interior`.
  * `boundary_tags`: List of the `2D` boundary tags. By default, periodic boundaries are tagged `:Dk_periodic` where `k` refers to the `k`th dimension, and aperiodic boundaries are tagged as `:Dk_inf`, `:Dk_sup` corresponding to the infimum and supremum in the `k`th dimension.
