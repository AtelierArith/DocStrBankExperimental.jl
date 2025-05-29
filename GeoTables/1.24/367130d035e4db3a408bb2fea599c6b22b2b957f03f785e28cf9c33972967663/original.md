```
geojoin(geotable₁, geotable₂, var₁ => agg₁, ..., varₙ => aggₙ; kind=:left, pred=intersects, on=nothing)
```

Joins `geotable₁` with `geotable₂` using a certain `kind` of join and predicate function `pred` that takes two geometries and returns a boolean (`(g1, g2) -> g1 ⊆ g2`).

Optionally, add a variable value match to join, in addition to geometric match, by passing a single name or list of variable names (strings or symbols) to the `on` keyword argument. The variable value match use the `isequal` function.

Whenever two or more matches are encountered, aggregate `varᵢ` with aggregation function `aggᵢ`. If no aggregation function is provided for a variable, then the aggregation function will be selected according to the scientific types: `mean` for continuous and `first` otherwise.

## Kinds

  * `:left` - Returns all rows of `geotable₁` filling entries with `missing` when there is no match in `geotable₂`.
  * `:inner` - Returns the subset of rows of `geotable₁` that has a match in `geotable₂`.

# Examples

```julia
geojoin(gtb1, gtb2)
geojoin(gtb1, gtb2, 1 => mean)
geojoin(gtb1, gtb2, :a => mean, :b => std)
geojoin(gtb1, gtb2, "a" => mean, pred=issubset)
geojoin(gtb1, gtb2, on=:a)
geojoin(gtb1, gtb2, kind=:inner, on=["a", "b"])
```

See also [`tablejoin`](@ref).
