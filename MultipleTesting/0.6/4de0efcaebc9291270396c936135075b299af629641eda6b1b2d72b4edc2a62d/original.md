Higher criticism threshold

# Examples

```jldoctest
julia> pvals = PValues([0.001, 0.01, 0.03, 0.5]);

julia> estimate(pvals, HigherCriticismThreshold())
0.03
```

# References

Donoho, D., and Jin, J. (2008). Higher criticism thresholding: Optimal feature selection when useful features are rare and weak. PNAS 105, 14790–14795.

Klaus, B., and Strimmer, K. (2013). Signal identification for rare and weak features: higher criticism or false discovery rates? Biostatistics 14, 129–143.
