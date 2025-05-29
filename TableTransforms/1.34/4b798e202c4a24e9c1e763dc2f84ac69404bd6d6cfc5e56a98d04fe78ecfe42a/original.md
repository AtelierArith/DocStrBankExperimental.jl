```
DropMissing()
DropMissing(:)
```

Drop all rows with missing values in table.

```
DropMissing(col₁, col₂, ..., colₙ)
DropMissing([col₁, col₂, ..., colₙ])
DropMissing((col₁, col₂, ..., colₙ))
```

Drop all rows with missing values in selected columns `col₁`, `col₂`, ..., `colₙ`.

```
DropMissing(regex)
```

Drop all rows with missing values in columns that match with `regex`.

# Examples

```julia
DropMissing()
DropMissing("b", "c", "e")
DropMissing([2, 3, 5])
DropMissing((:b, :c, :e))
DropMissing(r"[bce]")
```

## Notes

  * The transform can alter the element type of columns from `Union{Missing,T}` to `T`.
  * If the transformed column has only `missing` values, it will be converted to an empty column of type `Any`.
