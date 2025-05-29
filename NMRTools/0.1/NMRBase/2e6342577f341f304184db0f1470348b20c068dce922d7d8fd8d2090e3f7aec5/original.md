```
spin(n::Nucleus)
```

Return the spin quantum number of nucleus `n`, or `nothing` if not defined.

# Examples

```jldoctest
julia> spin(H1)
1//2
```

See also [`Coherence`](@ref).
