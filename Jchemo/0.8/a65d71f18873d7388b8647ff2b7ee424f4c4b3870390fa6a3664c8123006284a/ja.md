```
pval(d::Distribution, q)
pval(x::Array, q)
pval(e_cdf::ECDF, q)
```

分布、ECDF、またはベクトルのp値を計算します。

  * `d` : `Distribution.jl`から計算された分布。
  * `x` : 一変量データ。
  * `e_cdf` : `StatsBase.jl`から計算されたECDF。
  * `q` : p値を計算するための値。

量子 `q` のp値を計算または推定します。すなわち、V(Q > `q`) であり、ここで Q は確率変数です。

## 例

```julia
using Jchemo, Distributions, StatsBase

d = Distributions.Normal(0, 1)
q = 1.96
#q = [1.64; 1.96]
Distributions.cdf(d, q)    # 累積密度関数 (CDF)
Distributions.ccdf(d, q)   # 補完CDF (CCDF)
pval(d, q)                 # Distributions.ccdf

x = rand(5)
e_cdf = StatsBase.ecdf(x)
e_cdf(x)                # xの各点で計算された経験的CDF (ECDF)
p_val = 1 .- e_cdf(x)   # xの各点での補完ECDF
q = .3
#q = [.3; .5; 10]
pval(e_cdf, q)          # 1 .- e_cdf(q)
pval(x, q)
```
