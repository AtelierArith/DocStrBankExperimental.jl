```
Collect(X₁, X₂ … Xₙ) :: Query
```

In the combinator form, `Collect(X₁, X₂ … Xₙ)` adds fields `X₁`, `X₂` … `Xₙ` to the input record.

```jldoctest
julia> unitknot[Record(:x => 1) >> Collect(:y => 2 .* It.x)]
│ x  y │
┼──────┼
│ 1  2 │
```

If a field already exists, it is replaced.

```jldoctest
julia> unitknot[Record(:x => 1) >> Collect(:x => 2 .* It.x)]
│ x │
┼───┼
│ 2 │
```

To remove a field, assign it the value `nothing`.

```jldoctest
julia> unitknot[Record(:x => 1) >> Collect(:y => 2 .* It.x, :x => nothing)]
│ y │
┼───┼
│ 2 │
```

---

```
Each(X >> Record) :: Query
```

In the query form, `Collect` appends a field to the source record.

```jldoctest
julia> unitknot[Lift(1) >> Label(:x) >> Collect]
│ x │
┼───┼
│ 1 │
```
