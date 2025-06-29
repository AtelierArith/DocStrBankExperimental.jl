```
ZScore()
```

Applies the z-score transform (a.k.a. normal score) to all columns of the table. The z-score transform of the column `x`, with mean `μ` and standard deviation `σ`, is defined by `(x .- μ) ./ σ`.

```
ZScore(col₁, col₂, ..., colₙ)
ZScore([col₁, col₂, ..., colₙ])
ZScore((col₁, col₂, ..., colₙ))
```

Applies the ZScore transform on columns `col₁`, `col₂`, ..., `colₙ`.

```
ZScore(regex)
```

Applies the ZScore transform on columns that match with `regex`.

# Examples

```julia
ZScore(1, 3, 5)
ZScore([:a, :c, :e])
ZScore(("a", "c", "e"))
ZScore(r"[ace]")
```
