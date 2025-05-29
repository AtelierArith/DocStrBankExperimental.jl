```
Quantile(; dist=Normal())
```

The quantile transform to a given `distribution`.

```
Quantile(col₁, col₂, ..., colₙ; dist=Normal())
Quantile([col₁, col₂, ..., colₙ]; dist=Normal())
Quantile((col₁, col₂, ..., colₙ); dist=Normal())
```

Applies the Quantile transform on columns `col₁`, `col₂`, ..., `colₙ`.

```
Quantile(regex; dist=Normal())
```

Applies the Quantile transform on columns that match with `regex`.

# Examples

```julia
using Distributions

Quantile()
Quantile(dist=Normal())
Quantile(1, 3, 5, dist=Beta())
Quantile([:a, :c, :e], dist=Gamma())
Quantile(("a", "c", "e"), dist=Beta())
Quantile(r"[ace]", dist=Normal())
```
