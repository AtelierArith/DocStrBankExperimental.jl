```
LowHigh(; low=0.25, high=0.75)
```

Applies the LowHigh transform to all columns of the table. The LowHigh transform of the column `x` is defined by `(x .- xl) ./ (xh - xl)`, where `xl = quantile(x, low)` and `xh = quantile(x, high)`.

```
LowHigh(col₁, col₂, ..., colₙ; low=0.25, high=0.75)
LowHigh([col₁, col₂, ..., colₙ]; low=0.25, high=0.75)
LowHigh((col₁, col₂, ..., colₙ); low=0.25, high=0.75)
```

Applies the LowHigh transform on columns `col₁`, `col₂`, ..., `colₙ`.

```
LowHigh(regex; low=0.25, high=0.75)
```

Applies the LowHigh transform on columns that match with `regex`.

# Examples

```julia
LowHigh()
LowHigh(low=0, high=1)
LowHigh(low=0.3, high=0.7)
LowHigh(1, 3, 5, low=0, high=1)
LowHigh([:a, :c, :e], low=0.3, high=0.7)
LowHigh(("a", "c", "e"), low=0.25, high=0.75)
LowHigh(r"[ace]", low=0.3, high=0.7)
```
