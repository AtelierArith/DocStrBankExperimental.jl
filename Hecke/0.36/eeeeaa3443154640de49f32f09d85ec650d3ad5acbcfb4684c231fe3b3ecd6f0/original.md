```
multiplicity(s::MSet{T}, x::T) -> Int
```

Return the multiplicity of the element `x` in the multi-set `s`. If `x` is not in `s`, return 0.

# Examples

```jldoctest
julia> m = multiset([1,1,2,3,4,4,5])
MSet{Int64} with 7 elements:
  5
  4 : 2
  2
  3
  1 : 2

julia> multiplicity(m, 2)
1

julia> multiplicity(m, 6)
0
```
