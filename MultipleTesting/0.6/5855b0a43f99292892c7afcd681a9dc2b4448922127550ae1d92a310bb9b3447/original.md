Censored Beta-Uniform Mixture (censored BUM) π₀ estimator

# Examples

```jldoctest
julia> pvals = PValues([0.001, 0.002, 0.01, 0.03, 0.5]);

julia> estimate(pvals, CensoredBUM())
0.21052495526400936

```

# References

Markitsis, A., and Lai, Y. (2010). A censored beta mixture model for the estimation of the proportion of non-differentially expressed genes. Bioinformatics 26, 640–646.
