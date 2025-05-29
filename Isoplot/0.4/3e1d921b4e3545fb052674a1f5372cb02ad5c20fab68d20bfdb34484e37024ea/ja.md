```julia
metropolis_minmax(nsteps::Integer, dist::Collection, data::Collection{<:Measurement}; burnin::Integer=0)
metropolis_minmax(nsteps::Integer, dist::AbstractArray, data::AbstractArray, uncert::AbstractArray; burnin::Integer=0)
```

有限範囲のソース分布 `dist` の極値を推定するために、サンプルをその分布から引き出してメトロポリスサンプラーを実行します。例えば、ジルコンの結晶化年齢の分布からジルコンの飽和と噴火年齢を推定します。

### 例

```julia
tmindist, tmaxdist, lldist, acceptancedist = metropolis_minmax(2*10^5, MeltsVolcanicZirconDistribution, mu, sigma, burnin=10^5)
```
