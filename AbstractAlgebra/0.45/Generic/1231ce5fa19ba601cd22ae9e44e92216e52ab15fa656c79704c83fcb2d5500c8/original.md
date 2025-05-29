```
collength(Y::YoungTableau, i, j)
```

Return the column length of `Y` at box `(i,j)`, i.e. the number of boxes in the `j`-th column of the diagram of `Y` located below of the `(i,j)`-th box.

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

julia> Generic.collength(y, 1,1)
2

julia> Generic.collength(y, 1,3)
1

julia> Generic.collength(y, 2,4)
0
```
