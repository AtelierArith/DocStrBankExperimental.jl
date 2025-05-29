```
@rotate_orbs(orb1, orb2, angle, kwargs...)
```

Rotate orbitals `orb1` and `orb2` from [`WfOptions.orb`](@ref ECInfos.WfOptions)    by `angle` (in degrees). For UHF, `spin` can be `:α` or `:β` (keyword argument).

The orbitals are stored to [`WfOptions.orb`](@ref ECInfos.WfOptions).

# Keyword arguments

  * `spin::Symbol`: spin of the orbitals (default: `:α`).

# Examples

```julia
@dfhf
# swap orbitals 1 and 2
@rotate_orbs 1, 2, 90
```
