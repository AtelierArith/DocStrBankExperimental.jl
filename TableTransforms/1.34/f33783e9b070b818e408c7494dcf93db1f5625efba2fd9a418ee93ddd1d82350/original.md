```
DropNaN()
DropNaN(:)
```

Drop all rows with NaN values in table.

```
DropNaN(col₁, col₂, ..., colₙ)
DropNaN([col₁, col₂, ..., colₙ])
DropNaN((col₁, col₂, ..., colₙ))
```

Drop all rows with NaN values in selected columns `col₁`, `col₂`, ..., `colₙ`.

```
DropNaN(regex)
```

Drop all rows with NaN values in columns that match with `regex`.

# Examples

```julia
DropNaN(2, 3, 4)
DropNaN([:b, :c, :d])
DropNaN(("b", "c", "d"))
DropNaN(r"[bcd]")
```
