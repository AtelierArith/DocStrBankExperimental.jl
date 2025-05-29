BulkAndTailsDist(κ₀,τ₀,ϕ₀,κ₁,τ₁,ϕ₁,ν) *バルク・アンド・テール (BATs) 分布* の累積分布関数は

$$
F(x) = T_ν(H(x))
$$

であり、ここで T_ν は ν 自由度のスチューデントt分布の累積分布関数で、H は単調増加関数です。ϕ₀ と ϕ₁ は下側および上側テールの位置パラメータです。τ₀ と τ₁ は下側および上側テールのスケールパラメータです。κ₀ と κ₁ は下側および上側テールの形状パラメータです。負の κ は制約のあるテールを示します。正の κ は重いテールを示します。κ=0 の場合は、連続性によって定義され、薄いガウスのテールを示します。

`fitbats` はこれらのパラメータの最大尤度推定を提供します。さらに、`BulkAndTailsDist` のために `pdf`、`cdf`、`logpdf`、`logcdf`、`quantile`、および `rand` 関数を提供しており、これらはすべて `Distributions.jl` フレームワークに従っています。また、これらの関数のRフレンドリーなバージョンも提供し、Rからの呼び出し方法を示します。

```julia
BulkAndTailsDist(κ₀,τ₀,ϕ₀,κ₁,τ₁,ϕ₁,ν)     # BATs distribution
params(d)        # Get the parameters
minimum(d)       # lower bound of support
maximum(d)       # upper bound of support
```

外部リンク

  * [Stein, M. L. (2021).  A parametric model for distributions with flexible behavior in both tails. Environmetrics, 32(2):Paper No. e2658, 24.](https://onlinelibrary.wiley.com/doi/abs/10.1002/env.2658)
