```
tablejoin(geotable, table, var₁ => agg₁, ..., varₙ => aggₙ; kind=:left, on)
```

Joins `geotable` with `table` using the values of the `on` variables to match rows with a certain `kind` of join.

`on` variables can be a single name or list of variable names (strings or symbols). The variable value match use the `isequal` function.

Whenever two or more matches are encountered, aggregate `varᵢ` with aggregation function `aggᵢ`. If no aggregation function is provided for a variable, then the aggregation function will be selected according to the scientific types: `mean` for continuous and `first` otherwise.

## Kinds

  * `:left` - Returns all rows of `geotable` filling entries with `missing` when there is no match in `table`.
  * `:inner` - Returns the subset of rows of `geotable` that has a match in `table`.

# Examples

```julia
tablejoin(gtb, tab, on=:a)
tablejoin(gtb, tab, 1 => mean, on=:a)
tablejoin(gtb, tab, :a => mean, :b => std, on=:a)
tablejoin(gtb, tab, "a" => mean, on=[:a, :b])
tablejoin(gtb, tab, kind=:inner, on=["a", "b"])
```

See also [`geojoin`](@ref).
