```
Detrend(col₁, col₂, ..., colₙ; degree=1)
Detrend([col₁, col₂, ..., colₙ]; degree=1)
Detrend((col₁, col₂, ..., colₙ); degree=1)
```

The transform that detrends columns `col₁`, `col₂`, ..., `colₙ` with a polynomial of given `degree`.

```
Detrend(regex; degree=1)
```

Detrends the columns that match with `regex`.

# Examples

```julia
Detrend(1, 3, 5)
Detrend([:a, :c, :e])
Detrend(("a", "c", "e"))
Detrend(r"[ace]", degree=2)
Detrend(:)
```

## References

  * Menafoglio, A., Secchi, P. 2013. [A Universal Kriging predictor for spatially dependent functional data of a Hilbert Space](https://doi.org/10.1214/13-EJS843)
