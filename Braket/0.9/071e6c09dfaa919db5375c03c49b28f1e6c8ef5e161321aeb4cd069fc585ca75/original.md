```
(c::Circuit)(arg::Number; kwargs...)
(c::Circuit)(; kwargs...)
```

Fix all [`FreeParameter`](@ref)s in `c` as specified in `kwargs` and return a new circuit with the clamped parameters. `c` is unmodified.

If `arg` is passed, the values of all `FreeParameter`s *not* listed in `kwargs` will be set to `arg`.

# Examples

```jldoctest
julia> α = FreeParameter(:alpha);

julia> θ = FreeParameter(:theta);

julia> circ = Circuit();

julia> circ = H(circ, 0);

julia> circ = Rx(circ, 1, α);

julia> circ = Ry(circ, 0, θ);

julia> circ = Probability(circ);

julia> new_circ = circ(theta=2.0, alpha=1.0);
```
