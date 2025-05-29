```
Select(col₁, col₂, ..., colₙ)
Select([col₁, col₂, ..., colₙ])
Select((col₁, col₂, ..., colₙ))
```

The transform that selects columns `col₁`, `col₂`, ..., `colₙ`.

```
Select(col₁ => newcol₁, col₂ => newcol₂, ..., colₙ => newcolₙ)
```

Selects the columns `col₁`, `col₂`, ..., `colₙ` and rename them to `newcol₁`, `newcol₂`, ..., `newcolₙ`.

```
Select(regex)
```

Selects the columns that match with `regex`.

# Examples

```julia
Select(1, 3, 5)
Select([:a, :c, :e])
Select(("a", "c", "e"))
Select(1 => :x, 3 => :y)
Select(:a => :x, :b => :y)
Select("a" => "x", "b" => "y")
Select(r"[ace]")
```
