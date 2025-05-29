```
@combine(geotable, :col₁ = expr₁, :col₂ = expr₂, ..., :colₙ = exprₙ)
```

Returns geospatial `geotable` with columns `:col₁`, `:col₂`, ..., `:colₙ` computed with reduction expressions `expr₁`, `expr₂`, ..., `exprₙ`.

If a reduction expression is not defined for the `:geometry` column, the geometries will be reduced using `Multi`.

See also: [`@groupby`](@ref).

# Examples

```julia
@combine(geotable, :x_sum = sum(:x))
@combine(geotable, :x_mean = mean(:x))
@combine(geotable, :x_mean = mean(:x), :geometry = centroid(:geometry))

groups = @groupby(geotable, :y)
@combine(groups, :x_prod = prod(:x))
@combine(groups, :x_median = median(:x))
@combine(groups, :x_median = median(:x), :geometry = centroid(:geometry))

@combine(geotable, {"z"} = sum({"x"}) + prod({"y"}))
xnm, ynm, znm = :x, :y, :z
@combine(geotable, {znm} = sum({xnm}) + prod({ynm}))
```
