```
modeindex(mr::SphericalHarmonicModes.ModeRange, mode::Tuple)
```

Return the index of `mode` in the iterator `mr`. Raise an error if `mode` is not present in `mr`.

# Examples

```jldoctest
julia> r = LM(1:2, 1:2);

julia> collect(r)
3-element Vector{Tuple{Int64, Int64}}:
 (1, 1)
 (2, 1)
 (2, 2)

julia> modeindex(r, (2,1))
2

julia> modeindex(r, (3,2))
ERROR: Mode with (l=3,m=2) is not included in the range given by LM(1:2, 1:2)
```
