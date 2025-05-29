```
Take(N) :: Query
```

This query preserves the first `N` elements of its input, dropping the rest.

```jldoctest
julia> unitknot[Lift('a':'c') >> Take(2)]
──┼───┼
1 │ a │
2 │ b │
```

`Take(-N)` drops the last `N` elements.

```jldoctest
julia> unitknot[Lift('a':'c') >> Take(-2)]
──┼───┼
1 │ a │
```
