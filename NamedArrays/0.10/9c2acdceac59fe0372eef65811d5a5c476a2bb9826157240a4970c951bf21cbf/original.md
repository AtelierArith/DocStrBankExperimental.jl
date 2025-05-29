```
dimnames(n::NamedArray, [d::Integer])
```

Return the names of the `d`'th dimension of NamedArray `n`, or of all dimensions if `d` is unspecified.

# Example

```jldoctest
julia> n = NamedArray([1 2; 3 4; 5 6], (["一", "二", "三"], ["first", "second"]), ("cmn", "en"))
3×2 Named Matrix{Int64}
cmn ╲ en │  first  second
─────────┼───────────────
一       │      1       2
二       │      3       4
三       │      5       6

julia> dimnames(n)
2-element Vector{String}:
"cmn"
"en"
```
