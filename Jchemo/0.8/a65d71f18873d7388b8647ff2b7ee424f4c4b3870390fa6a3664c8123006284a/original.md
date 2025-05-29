```
pval(d::Distribution, q)
pval(x::Array, q)
pval(e_cdf::ECDF, q)
```

Compute p-value(s) for a distribution, an ECDF or vector.

  * `d` : A distribution computed from `Distribution.jl`.
  * `x` : Univariate data.
  * `e_cdf` : An ECDF computed from `StatsBase.jl`.
  * `q` : Value(s) for which to compute the p-value(s).

Compute or estimate the p-value of quantile `q`, ie. V(Q > `q`) where Q is the random variable.

## Examples

```julia
using Jchemo, Distributions, StatsBase

d = Distributions.Normal(0, 1)
q = 1.96
#q = [1.64; 1.96]
Distributions.cdf(d, q)    # cumulative density function (CDF)
Distributions.ccdf(d, q)   # complementary CDF (CCDF)
pval(d, q)                 # Distributions.ccdf

x = rand(5)
e_cdf = StatsBase.ecdf(x)
e_cdf(x)                # empirical CDF computed at each point of x (ECDF)
p_val = 1 .- e_cdf(x)   # complementary ECDF at each point of x
q = .3
#q = [.3; .5; 10]
pval(e_cdf, q)          # 1 .- e_cdf(q)
pval(x, q)
```
