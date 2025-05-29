```julia
metropolis_min(nsteps::Integer, dist::Collection, data::Collection{<:Measurement}; burnin::Integer=0, t0prior=Uniform(0,minimum(value.(age68.(analyses)))), lossprior=Uniform(0,100))
metropolis_min(nsteps::Integer, dist::Collection, mu::AbstractArray, sigma::AbstractArray; burnin::Integer=0)
metropolis_min(nsteps::Integer, dist::Collection, analyses::Collection{<:UPbAnalysis; burnin::Integer=0)
```

有限範囲のソース分布 `dist` の最小値を推定するためにメトロポリスサンプラーを実行します。この分布から引き出されたサンプルを使用して、例えば、ジルコンの結晶化年齢の分布からジルコンの噴出年齢を推定します。

### 例

```julia
tmindist = metropolis_min(2*10^5, MeltsVolcanicZirconDistribution, mu, sigma, burnin=10^5)

tmindist, t0dist = metropolis_min(2*10^5, HalfNormalDistribution, analyses, burnin=10^5)
```
