```
It :: AbstractQuery
```

In a query expression, use `It` to refer to the query's input.

```jldoctest
julia> unitknot[Lift(3) >> (It .+ 1)]
┼───┼
│ 4 │
```

`It` is the identity with respect to query composition.

```jldoctest
julia> unitknot[Lift('a':'c') >> It]
──┼───┼
1 │ a │
2 │ b │
3 │ c │
```

`It` provides a shorthand notation for data navigation using `Get`, so that `It.a.x` is equivalent to `Get(:a) >> Get(:x)`.

```jldoctest
julia> unitknot[Lift((a=(x=1,y=2),)) >> It.a]
│ a    │
│ x  y │
┼──────┼
│ 1  2 │

julia> unitknot[Lift((a=(x=1,y=2),)) >> It.a.x]
│ x │
┼───┼
│ 1 │
```
