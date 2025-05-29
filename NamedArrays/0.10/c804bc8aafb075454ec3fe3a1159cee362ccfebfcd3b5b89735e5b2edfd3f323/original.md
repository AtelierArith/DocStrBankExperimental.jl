```
setdimnames!(n::NamedArray, name, d::Integer)
```

Set the name of the dimension `d` of NamedArray `n` to `name`. 

# Example

```jldoctest
julia> n = NamedArray([1 2 3; 4 5 6])
2×3 Named Matrix{Int64}
A ╲ B │ 1  2  3
──────┼────────
1     │ 1  2  3
2     │ 4  5  6

julia> setdimnames!(n, :second, 2)
(:A, :second)

julia> n
2×3 Named Matrix{Int64}
A ╲ second │ 1  2  3
───────────┼────────
1          │ 1  2  3
2          │ 4  5  6
```
