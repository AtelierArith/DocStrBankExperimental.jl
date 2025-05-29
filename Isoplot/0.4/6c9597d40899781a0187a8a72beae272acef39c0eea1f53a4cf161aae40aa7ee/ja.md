```julia
metropolis_minmax!(tmindist, tmaxdist, lldist, acceptancedist, nsteps::Integer, dist::AbstractArray, data::AbstractArray, uncert::AbstractArray; burnin::Integer=0)
metropolis_minmax!(tmindist, tmaxdist, t0dist, lldist, acceptancedist, nsteps::Integer, dist::Collection, analyses::Collection{<:UPbAnalysis}; burnin::Integer=0)
```

既存の配列を埋めるインプレース（非アロケーション）バージョンの `metropolis_minmax`

サンプルを使用して有限範囲のソース分布 `dist` の極値を推定するためにメトロポリスサンプラーを実行します。例えば、ジルコンの結晶化年齢の分布からジルコンの飽和と噴火年齢を推定します。

### 例

```julia
metropolis_minmax!(tmindist, tmaxdist, lldist, acceptancedist, 2*10^5, MeltsVolcanicZirconDistribution, mu, sigma, burnin=10^5)
```
