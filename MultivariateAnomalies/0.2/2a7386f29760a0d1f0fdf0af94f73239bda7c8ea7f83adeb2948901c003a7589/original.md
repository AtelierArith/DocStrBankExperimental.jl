```
EWMA(dat,  λ)
```

Compute the exponential weighted moving average (EWMA) with the weighting parameter `λ` between 0 (full weighting) and 1 (no weighting) along the first dimension of `dat`. Supports N-dimensional Arrays.

Lowry, C. A., & Woodall, W. H. (1992). A Multivariate Exponentially Weighted Moving Average Control Chart. Technometrics, 34, 46–53.

# Examples

```
julia> dc = rand(100,3,2)
julia> ewma_dc = EWMA(dc, 0.1)
```
