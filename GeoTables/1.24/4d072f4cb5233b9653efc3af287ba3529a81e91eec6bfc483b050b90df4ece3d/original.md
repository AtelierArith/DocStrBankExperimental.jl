```
@groupby(geotable, col₁, col₂, ..., colₙ)
@groupby(geotable, [col₁, col₂, ..., colₙ])
@groupby(geotable, (col₁, col₂, ..., colₙ))
```

Group geospatial `geotable` by columns `col₁`, `col₂`, ..., `colₙ`.

```
@groupby(geotable, regex)
```

Group geospatial `geotable` by columns that match with `regex`.

# Examples

```julia
@groupby(geotable, 1, 3, 5)
@groupby(geotable, [:a, :c, :e])
@groupby(geotable, ("a", "c", "e"))
@groupby(geotable, r"[ace]")
```
