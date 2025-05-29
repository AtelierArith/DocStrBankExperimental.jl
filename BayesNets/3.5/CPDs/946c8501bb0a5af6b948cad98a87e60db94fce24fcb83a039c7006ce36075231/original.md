A linear Gaussian CPD, always returns a Normal

```
Assumes that target and all parents can be converted to Float64 (ie, are numeric)

P(x|parents(x)) = Normal(μ=a×parents(x) + b, σ)
```
