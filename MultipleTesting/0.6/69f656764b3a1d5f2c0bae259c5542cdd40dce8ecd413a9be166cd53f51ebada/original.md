Storey's closed-form bootstrap π₀ estimator

# Examples

```jldoctest
julia> pvals = PValues([0.001, 0.002, 0.01, 0.03, 0.5]);

julia> estimate(pvals, StoreyBootstrap())
0.0

julia> estimate(pvals, StoreyBootstrap(0.1:0.1:0.9, 0.2))
0.0
```

# References

Robinson, D. (2016). Original Procedure for Choosing λ. http://varianceexplained.org/files/pi0boot.pdf

Storey, J.D., Taylor, J.E., and Siegmund, D. (2004). Strong control, conservative point estimation and simultaneous conservative consistency of false discovery rates: a unified approach. Journal of the Royal Statistical Society: Series B (Statistical Methodology) 66, 187–205.
