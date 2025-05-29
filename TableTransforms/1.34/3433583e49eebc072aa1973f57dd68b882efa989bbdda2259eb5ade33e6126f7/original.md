```
MinMax()
```

Applies the MinMax transform to all columns of the table. The MinMax transform is equivalent to `LowHigh(low=0, high=1)`.

```
MinMax(col₁, col₂, ..., colₙ)
MinMax([col₁, col₂, ..., colₙ])
MinMax((col₁, col₂, ..., colₙ))
```

Applies the MinMax transform on columns `col₁`, `col₂`, ..., `colₙ`.

```
MinMax(regex)
```

Applies the MinMax transform on columns that match with `regex`.

# Examples

```julia
MinMax(1, 3, 5)
MinMax([:a, :c, :e])
MinMax(("a", "c", "e"))
MinMax(r"[ace]")
```

See also [`LowHigh`](@ref).
