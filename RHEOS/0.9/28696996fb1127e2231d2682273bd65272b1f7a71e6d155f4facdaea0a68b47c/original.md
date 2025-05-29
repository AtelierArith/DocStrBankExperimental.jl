```
freezeparams(m::RheoModelClass, nt0::NamedTuple)
```

Return a new `RheoModelClass` with some of the parameters frozen to specific values

# Arguments

  * `m`: original `RheoModelClass`
  * `nt0`: named tuple with values for each parameter to freeze

# Example

```@example
julia> SLS2_mod = freezeparams( SLS2, (G₀=2,η₂=3.5))
[...]

julia> SLS2.G(1,[2,1,2,3,3.5])
3.8796492

julia> SLS2_mod.G(1,[1,2,3])
3.8796492
```
