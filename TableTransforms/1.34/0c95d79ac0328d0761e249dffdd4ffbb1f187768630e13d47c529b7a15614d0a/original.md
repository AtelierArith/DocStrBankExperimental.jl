```
DropUnits()
DropUnits(:)
```

Drop units from all columns in the table.

```
DropUnits(col₁, col₂, ..., colₙ)
DropUnits([col₁, col₂, ..., colₙ])
DropUnits((col₁, col₂, ..., colₙ))
```

Drop units from selected columns `col₁`, `col₂`, ..., `colₙ`.

```
DropUnits(regex)
```

Drop units from columns that match with `regex`.

# Examples

```julia
DropUnits()
DropUnits([2, 3, 5])
DropUnits([:b, :c, :e])
DropUnits(("b", "c", "e"))
DropUnits(r"[bce]")
```
