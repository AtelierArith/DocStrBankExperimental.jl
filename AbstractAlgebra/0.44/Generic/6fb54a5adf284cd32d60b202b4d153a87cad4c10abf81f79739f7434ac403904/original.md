```
hooklength(Y::YoungTableau, i, j)
```

Return the hook-length of an element in `Y` at position `(i,j)`, i.e the number of cells in the `i`-th row to the right of `(i,j)`-th box, plus the number of cells in the `j`-th column below the `(i,j)`-th box, plus `1`.

Return `0` for `(i,j)` not in the tableau `Y`.

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

julia> hooklength(y, 1,1)
6

julia> hooklength(y, 1,3)
3

julia> hooklength(y, 2,4)
0
```
