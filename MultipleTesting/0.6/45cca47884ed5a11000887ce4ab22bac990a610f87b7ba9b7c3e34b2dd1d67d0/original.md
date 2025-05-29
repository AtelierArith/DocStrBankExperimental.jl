Flat Grenander π₀ estimator

Estimates π₀ by finding the longest constant interval in the Grenander estimator.

# Examples

```jldoctest
julia> pvals = PValues([0.001, 0.002, 0.01, 0.03, 0.5]);

julia> estimate(pvals, FlatGrenander())
0.42553191489361697
```

# References

Langaas, M., Lindqvist, B.H., and Ferkingstad, E. (2005). Estimating the proportion of true null hypotheses, with application to DNA microarray data. Journal of the Royal Statistical Society: Series B (Statistical Methodology) 67, 555–572.
