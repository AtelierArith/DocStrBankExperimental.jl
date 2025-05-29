```
@transform(geotable, :col₁ = expr₁, :col₂ = expr₂, ..., :colₙ = exprₙ)
```

Returns geospatial `geotable` with columns `col₁`, `col₂`, ..., `colₙ` computed with expressions `expr₁`, `expr₂`, ..., `exprₙ`.

See also: [`@groupby`](@ref).

# Examples

```julia
@transform(geotable, :z = :x + 2*:y)
@transform(geotable, :w = :x^2 - :y^2)
@transform(geotable, :sinx = sin(:x), :cosy = cos(:y))

groups = @groupby(geotable, :y)
@transform(groups, :logx = log(:x))
@transform(groups, :expz = exp(:z))

@transform(geotable, {"z"} = {"x"} - 2*{"y"})
xnm, ynm, znm = :x, :y, :z
@transform(geotable, {znm} = {xnm} - 2*{ynm})
```
