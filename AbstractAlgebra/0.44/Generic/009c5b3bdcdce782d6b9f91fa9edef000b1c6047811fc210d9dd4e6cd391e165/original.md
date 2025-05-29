```
getindex(Y::YoungTableau, n::Integer)
```

Return the column-major linear index into the `size(Y)`-array. If a box is outside of the array return `0`.

# Examples

```jldoctest
julia> y = YoungTableau([4,3,1])
┌───┬───┬───┬───┐
│ 1 │ 2 │ 3 │ 4 │
├───┼───┼───┼───┘
│ 5 │ 6 │ 7 │
├───┼───┴───┘
│ 8 │
└───┘

julia> y[1]
1

julia> y[2]
5

julia> y[4]
2

julia> y[6]
0
```
