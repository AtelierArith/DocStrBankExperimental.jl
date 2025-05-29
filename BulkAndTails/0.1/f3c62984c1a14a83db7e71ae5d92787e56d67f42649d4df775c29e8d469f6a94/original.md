BulkAndTailsDist(κ₀,τ₀,ϕ₀,κ₁,τ₁,ϕ₁,ν) The *Bulk-And-Tails (BATs) distribution* has cumulative distribution function

$$
F(x) = T_ν(H(x))
$$

where T_ν is the student-t cdf with ν degrees of freedom and H is a monotone increasing function. ϕ₀ and ϕ₁ are location parameters for the lower and upper tails. τ₀ and τ₁ are scale parameters for the lower and upper tails. κ₀ and κ₁ are shape parameters for the lower and upper tails. Negative κ indicates a bounded tail. Positive κ indicates a heavy tail. The case κ=0, defined by continuity, indicates a thin Gaussian tail.

`fitbats` provides maximum likelihood estimation for these parameters. In addition, we provide  `pdf`, `cdf`, `logpdf`, `logcdf`, `quantile`, and `rand` functions for `BulkAndTailsDist`, all of which follow the  `Distributions.jl` framework. We also provide R-friendly versions of these functions and show how to call them from R.

```julia
BulkAndTailsDist(κ₀,τ₀,ϕ₀,κ₁,τ₁,ϕ₁,ν)     # BATs distribution
params(d)        # Get the parameters
minimum(d)       # lower bound of support
maximum(d)       # upper bound of support
```

External links

  * [Stein, M. L. (2021).  A parametric model for distributions with flexible behavior in both tails. Environmetrics, 32(2):Paper No. e2658, 24.](https://onlinelibrary.wiley.com/doi/abs/10.1002/env.2658)
