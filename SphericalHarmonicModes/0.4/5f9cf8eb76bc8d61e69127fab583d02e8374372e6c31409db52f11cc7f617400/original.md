```
m_range(mr::SphericalHarmonicModes.SHModeRange, l::Integer)
```

Return the subsection of the range of `m` spanned by the iterator for which `(l,m)` is a valid spherical harmonic mode.

# Examples

```jldoctest
julia> r = LM(1:2, 1:2);

julia> collect(r)
3-element Vector{Tuple{Int64, Int64}}:
 (1, 1)
 (2, 1)
 (2, 2)

julia> m_range(r, 1)
1:1

julia> m_range(r, 2)
1:2
```
