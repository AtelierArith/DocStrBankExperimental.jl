```
names(n::NamedArray, [d::Integer])
```

Extract the names of the indices along dimension `d`, or all dimentsions if `d` is unspecified.

# Example

```jldoctest
julia> n = NamedArray([1, 2, 3], (["one", "二", "trois"],))
3-element Named Vector{Int64}
A     │ 
──────┼──
one   │ 1
二    │ 2
trois │ 3

julia> names(n)
1-element Vector{Vector{String}}:
    ["one", "二", "trois"]
```
