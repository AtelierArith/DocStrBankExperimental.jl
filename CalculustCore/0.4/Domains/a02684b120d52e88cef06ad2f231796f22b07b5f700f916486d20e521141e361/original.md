```julia
FourierDomain(D; kwargs...)

```

Creates a `D`-dimensional box domain that is periodic in all directions. The domain spans from `-π` to `π` in each dimension.

# Keyword Arguments

  * `periodic_dims`: List of periodic dimensions in `1:D`. Defaults to none.
  * `tag`: Domain tag (symbol) defaults to `:Interior`.
  * `boundary_tags`: List of the `2D` boundary tags. By default, periodic boundaries are tagged `:Dk_periodic` where `k` refers to the `k`th dimension, and aperiodic boundaries are tagged as `:Dk_inf`, `:Dk_sup` corresponding to the infimum and supremum in the `k`th dimension.
