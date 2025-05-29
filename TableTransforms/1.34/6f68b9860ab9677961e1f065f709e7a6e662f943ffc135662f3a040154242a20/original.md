```
Reject(col₁, col₂, ..., colₙ)
Reject([col₁, col₂, ..., colₙ])
Reject((col₁, col₂, ..., colₙ))
```

The transform that discards columns `col₁`, `col₂`, ..., `colₙ`.

```
Reject(regex)
```

Discards the columns that match with `regex`.

# Examples

```julia
Reject(:b, :d, :f)
Reject(["b", "d", "f"])
Reject((2, 4, 6))
Reject(r"[bdf]")
```
