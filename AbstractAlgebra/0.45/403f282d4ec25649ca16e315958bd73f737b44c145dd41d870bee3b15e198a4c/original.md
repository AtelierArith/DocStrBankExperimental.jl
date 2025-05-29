```
is_nilpotent(a::T) where {T <: NCRingElement}
```

Return true iff $a$ is nilpotent, i.e. a^k == 0 for some k.

# Examples

```jldoctest
julia> R, _ = residue_ring(ZZ,720);

julia> S, x = polynomial_ring(R, :x);

julia> is_nilpotent(30*x), is_nilpotent(30+90*x), is_nilpotent(S(15))
(true, true, false)
```
