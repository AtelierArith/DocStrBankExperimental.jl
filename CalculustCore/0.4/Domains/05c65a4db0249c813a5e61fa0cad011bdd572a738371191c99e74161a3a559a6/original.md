```julia
BoxDomain(endpoints; periodic_dims, tag, boundary_tags)

```

Creates a `D`-dimensional box domain with endpoints given by `endpoints`

# Keyword Arguments

  * `periodic_dims`: List of periodic dimensions in `1:D`. Defaults to none.
  * `tag`: Domain tag (symbol) defaults to `:Interior`.
  * `boundary_tags`: List of the `2D` boundary tags. By default, periodic boundaries are tagged `:Dk_periodic` where `k` refers to the `k`th dimension, and aperiodic boundaries are tagged as `:Dk_inf`, `:Dk_sup` corresponding to the infimum and supremum in the `k`th dimension.

# Example

```
julia> domain = BoxDomain(0, 1, 2, 3; periodic_dims=2)
(0, 1) × (2, 3)

julia> boundary_tags(domain)
(:D1_inf, :D1_sup, :D2_periodic, :D2_periodic)
```
