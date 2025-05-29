```
Join(X) :: Query
```

`Join(X)` evaluates `X` in the source context and adds it as a field to the input record.

```jldoctest
julia> unitknot[Record(:x => 1) >> Each(Record(:y => 2 .* It.x) >> Join(It.x))]
│ y  x │
┼──────┼
│ 2  1 │
```
