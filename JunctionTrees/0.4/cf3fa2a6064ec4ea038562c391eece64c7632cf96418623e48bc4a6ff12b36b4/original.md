```julia
redu(
    A::JunctionTrees.Factor{T},
    vars::Tuple,
    vals::Tuple
) -> JunctionTrees.Factor

```

Reduce/invalidate all entries in `A` that are not consitent with the evidence passed in `vars` and `vals`, where each variable in `vars` is assigned the corresponding value in `vals`.

# Examples

```jldoctest
A = Factor{Float64,3}((1, 2, 3), cat([0.25 0.08; 0.05 0.0; 0.15 0.09],
                                     [0.35 0.16; 0.07 0.0; 0.21 0.18], dims=3))
obs_vars = (3,)
obs_vals = (1,)
redu(A, obs_vars, obs_vals)

# output

Factor{Float64, 3}((1, 2, 3), [0.25 0.08; 0.05 0.0; 0.15 0.09;;; 0.0 0.0; 0.0 0.0; 0.0 0.0])
```
