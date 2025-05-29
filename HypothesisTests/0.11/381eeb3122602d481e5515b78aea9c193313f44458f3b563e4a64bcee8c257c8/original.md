```
BinomialTest(x::Integer, n::Integer, p::Real = 0.5)
BinomialTest(x::AbstractVector{Bool}, p::Real = 0.5)
```

Perform a binomial test of the null hypothesis that the distribution from which `x` successes were encountered in `n` draws (or alternatively from which the vector `x` was drawn) has success probability `p` against the alternative hypothesis that the success probability is not equal to `p`.

Computed confidence intervals by default are Clopper-Pearson intervals. See the [`confint(::BinomialTest)`](@ref) documentation for a list of supported methods to compute confidence intervals.

Implements: [`pvalue`](@ref), [`confint(::BinomialTest)`](@ref)
