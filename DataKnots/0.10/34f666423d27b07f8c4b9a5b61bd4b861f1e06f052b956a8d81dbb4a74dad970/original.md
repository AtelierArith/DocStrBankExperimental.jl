```
Each(X) :: Query
```

This evaluates `X` elementwise.

```jldoctest
julia> X = Lift('a':'c') >> Count;

julia> unitknot[Lift(1:3) >> Each(X)]
──┼───┼
1 │ 3 │
2 │ 3 │
3 │ 3 │
```

Compare this with the query without `Each`.

```jldoctest
julia> X = Lift('a':'c') >> Count;

julia> unitknot[Lift(1:3) >> X]
┼───┼
│ 9 │
```
