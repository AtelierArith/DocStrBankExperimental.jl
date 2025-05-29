Simes's p-value combination

# Examples

```jldoctest
julia> pvals = PValues([0.01, 0.02, 0.3, 0.5]);

julia> combine(pvals, Simes())
0.04
```

# References

Simes, R.J. (1986). An improved Bonferroni procedure for multiple tests of significance. Biometrika 73, 751–754.
