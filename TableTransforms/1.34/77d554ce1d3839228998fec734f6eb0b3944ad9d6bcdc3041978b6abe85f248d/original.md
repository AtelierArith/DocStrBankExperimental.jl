```
Interquartile()
```

Applies the Interquartile transform to all columns of the table. The Interquartile transform is equivalent to `LowHigh(low=0.25, high=0.75)`.

```
Interquartile(col₁, col₂, ..., colₙ)
Interquartile([col₁, col₂, ..., colₙ])
Interquartile((col₁, col₂, ..., colₙ))
```

Applies the Interquartile transform on columns `col₁`, `col₂`, ..., `colₙ`.

```
Interquartile(regex)
```

Applies the Interquartile transform on columns that match with `regex`.

# Examples

```julia
Interquartile(1, 3, 5)
Interquartile([:a, :c, :e])
Interquartile(("a", "c", "e"))
Interquartile(r"[ace]")
```

See also [`LowHigh`](@ref).
