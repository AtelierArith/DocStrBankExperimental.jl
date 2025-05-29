```
Get(lbl::Symbol) :: Query
```

This query extracts a field value by its label.

```jldoctest
julia> unitknot[Lift((x=1, y=2)) >> Get(:x)]
│ x │
┼───┼
│ 1 │
```

This has a shorthand form using `It`.

```jldoctest
julia> unitknot[Lift((x=1, y=2)) >> It.x]
│ x │
┼───┼
│ 1 │
```

With unlabeled fields, ordinal labels (A, B, ...) can be used.

```jldoctest
julia> unitknot[Lift((1,2)) >> It.B]
┼───┼
│ 2 │
```
