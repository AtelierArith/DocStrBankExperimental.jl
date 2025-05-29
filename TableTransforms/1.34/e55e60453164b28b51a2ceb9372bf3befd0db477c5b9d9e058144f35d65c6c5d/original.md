```
AbsoluteUnits()
AbsoluteUnits(:)
```

Converts the units of all columns in the table to absolute units.

```
AbsoluteUnits(col₁, col₂, ..., colₙ)
AbsoluteUnits([col₁, col₂, ..., colₙ])
AbsoluteUnits((col₁, col₂, ..., colₙ))
```

Converts the units of selected columns `col₁`, `col₂`, ..., `colₙ` to absolute units.

```
AbsoluteUnits(regex)
```

Converts the units of columns that match with `regex` to absolute units.

# Examples

```julia
AbsoluteUnits()
AbsoluteUnits([2, 3, 5])
AbsoluteUnits([:b, :c, :e])
AbsoluteUnits(("b", "c", "e"))
AbsoluteUnits(r"[bce]")
```
