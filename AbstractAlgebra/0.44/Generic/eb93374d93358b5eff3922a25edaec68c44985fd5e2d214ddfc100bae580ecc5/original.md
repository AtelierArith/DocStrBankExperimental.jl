```
rowlength(Y::YoungTableau, i, j)
```

Return the row length of `Y` at box `(i,j)`, i.e. the number of boxes in the `i`-th row of the diagram of `Y` located to the right of the `(i,j)`-th box.

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

julia> Generic.rowlength(y, 1,2)
2

julia> Generic.rowlength(y, 2,3)
0

julia> Generic.rowlength(y, 3,3)
0
```
