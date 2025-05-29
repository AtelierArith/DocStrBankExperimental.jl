```
Filter(X) :: Query
```

This query emits the elements from its input that satisfy a given condition.

```jldoctest
julia> unitknot[Lift(1:5) >> Filter(isodd.(It))]
──┼───┼
1 │ 1 │
2 │ 3 │
3 │ 5 │
```

When the predicate query produces an empty output, the condition is presumed to have failed.

```jldoctest
julia> unitknot[Lift('a':'c') >> Filter(missing)]
(empty)
```

When the predicate produces plural output, the condition succeeds if at least one output value is `true`.

```jldoctest
julia> unitknot[Lift('a':'c') >> Filter([true,false])]
──┼───┼
1 │ a │
2 │ b │
3 │ c │
```
