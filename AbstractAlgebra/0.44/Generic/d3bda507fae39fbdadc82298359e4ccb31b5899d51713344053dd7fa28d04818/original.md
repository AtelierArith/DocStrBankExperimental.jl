```
conj(Y::YoungTableau)
```

Return the conjugated tableau, i.e. the tableau reflected through the main diagonal.

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

julia> conj(y)
┌───┬───┬───┐
│ 1 │ 5 │ 8 │
├───┼───┼───┘
│ 2 │ 6 │
├───┼───┤
│ 3 │ 7 │
├───┼───┘
│ 4 │
└───┘
```
