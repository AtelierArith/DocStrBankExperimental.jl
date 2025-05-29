```
Lift(val) :: Query
```

This converts any value to a constant query.

```jldoctest
julia> unitknot[Lift("Hello")]
┼───────┼
│ Hello │
```

`AbstractVector` objects become plural queries.

```jldoctest
julia> unitknot[Lift('a':'c')]
──┼───┼
1 │ a │
2 │ b │
3 │ c │
```

To specify the vector cardinality, add `:x0to1`, `:x0toN`, `:x1to1`, or `:x1toN`.

```jldoctest
julia> unitknot[Lift('a':'c', :x1toN)]
──┼───┼
1 │ a │
2 │ b │
3 │ c │
```

The `missing` value makes an query with no output.

```jldoctest
julia> unitknot[Lift(missing)]
(empty)
```
