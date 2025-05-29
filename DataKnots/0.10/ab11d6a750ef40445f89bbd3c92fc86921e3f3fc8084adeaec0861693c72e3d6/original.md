```
Drop(N) :: Query
```

This query drops the first `N` elements of its input, preserving the rest.

```jldoctest
julia> unitknot[Lift('a':'c') >> Drop(2)]
──┼───┼
1 │ c │
```

`Drop(-N)` takes the last `N` elements.

```jldoctest
julia> unitknot[Lift('a':'c') >> Drop(-2)]
──┼───┼
1 │ b │
2 │ c │
```
