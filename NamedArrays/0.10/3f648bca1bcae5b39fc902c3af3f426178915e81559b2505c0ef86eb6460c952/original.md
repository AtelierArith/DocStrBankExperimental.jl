```
setdimnames(n::NamedArray, dimnames::Vector)
```

Set the dimension names of NamedArray `n` to `dimnames`.

# Example

```jldoctest
julia> n = NamedArray([1 2; 3 4; 5 6])
3×2 Named Matrix{Int64}
A ╲ B │ 1  2
──────┼─────
1     │ 1  2
2     │ 3  4
3     │ 5  6

julia> setdimnames!(n, ["fist", "second"])
("fist", "second")

julia> n
3×2 Named Matrix{Int64}
fist ╲ second │ 1  2
──────────────┼─────
1             │ 1  2
2             │ 3  4
3             │ 5  6
```
