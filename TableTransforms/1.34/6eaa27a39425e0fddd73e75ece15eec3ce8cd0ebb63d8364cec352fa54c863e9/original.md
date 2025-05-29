```
Coalesce(; value)
```

Replaces all `missing` values from the table with `value`.

```
Coalesce(col₁, col₂, ..., colₙ; value)
Coalesce([col₁, col₂, ..., colₙ]; value)
Coalesce((col₁, col₂, ..., colₙ); value)
```

Replaces all missing values from the columns `col₁`, `col₂`, ..., `colₙ` with `value`.

```
Coalesce(regex; value)
```

Replaces all missing values from the columns that match with `regex` with `value`.

# Examples

```julia
Coalesce(value=0)
Coalesce(1, 3, 5, value=1)
Coalesce([:a, :c, :e], value=2)
Coalesce(("a", "c", "e"), value=3)
Coalesce(r"[ace]", value=4)
```

## Notes

  * The transform can alter the element type of columns from `Union{Missing,T}` to `T`.
