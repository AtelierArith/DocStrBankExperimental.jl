```
DropExtrema(; low=0.25, high=0.75)
```

Drops rows where any of the values in all columns are outside the interval (`[quantile(col, low), quantile(col, high)]`).

```
DropExtrema(col₁, col₂, ..., colₙ; low=0.25, high=0.75)
DropExtrema([col₁, col₂, ..., colₙ]; low=0.25, high=0.75)
DropExtrema((col₁, col₂, ..., colₙ); low=0.25, high=0.75)
```

Drops rows where any of the values in columns `col₁`, `col₂`, ..., `colₙ` are outside the interval.

```
DropExtrema(regex; low=0.25, high=0.75)
```

Drops rows where any of the values in columns that match with `regex` are outside the interval.

# Examples

```julia
DropExtrema(low=0.3, high=0.7)
DropExtrema(1, low=0.3, high=0.7)
DropExtrema(:a, low=0.2, high=0.8)
DropExtrema("a", low=0.3, high=0.7)
DropExtrema(1, 3, 5, low=0, high=1)
DropExtrema([:a, :c, :e], low=0.3, high=0.7)
DropExtrema(("a", "c", "e"), low=0.25, high=0.75)
DropExtrema(r"[ace]", low=0.3, high=0.7)
```
