Right boundary π₀ estimator

# Examples

```jldoctest
julia> pvals = PValues([0.001, 0.002, 0.01, 0.03, 0.5]);

julia> estimate(pvals, RightBoundary())
0.2127659574468085

julia> estimate(pvals, RightBoundary(0.1:0.1:0.9))
0.25
```

# References

Liang, K., and Nettleton, D. (2012). Adaptive and dynamic adaptive procedures for false discovery rate control and estimation. Journal of the Royal Statistical Society: Series B (Statistical Methodology) 74, 163–182.
