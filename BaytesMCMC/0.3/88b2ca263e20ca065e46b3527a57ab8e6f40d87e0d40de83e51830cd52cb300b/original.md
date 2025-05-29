```julia
combine_turn_statistics(trajectory, x, y)

```

Combine turn statistics on trajectory. Implementation can assume that the trees that correspond to the turn statistics have the same ordering. When

```julia
τ = combine_turn_statistics(trajectory, τ₁, τ₂)
is_turning(trajectory, τ)
```

the combined turn statistic `τ` is guaranteed not to escape the caller, so it can eg change type.

# Examples

```julia

```
