Logit p-value combination

# Examples

```jldoctest
julia> pvals = PValues([0.01, 0.02, 0.3, 0.5]);

julia> combine(pvals, Logit())
0.006434494635148462
```

# References

Mudholkar, G.S., and George, E.O. (1977). The Logit Statistic for Combining Probabilities - An Overview (Rochester University NY, Dept of Statistics).
