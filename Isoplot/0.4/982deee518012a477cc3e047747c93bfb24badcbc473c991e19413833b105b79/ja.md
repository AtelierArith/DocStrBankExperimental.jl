```julia
metropolis_min!(tmindist::DenseArray, dist::Collection, mu::AbstractArray, sigma::AbstractArray; burnin::Integer=0)
metropolis_min!(tmindist::DenseArray, t0dist::DenseArray, dist::Collection, analyses::Collection{<:UPbAnalysis}; burnin::Integer=0) where {T}
```

インプレース（非アロケーション）バージョンの `metropolis_min` は、既存の配列 `tmindist` を埋めます。

メトロポリスサンプラーを実行して、サンプルが引き出された有限範囲のソース分布 `dist` の最小値を推定します。例えば、ジルコンの結晶化年齢の分布からジルコンの噴火年齢を推定します。

### 例

```julia
metropolis_min!(tmindist, 2*10^5, MeltsVolcanicZirconDistribution, mu, sigma, burnin=10^5)
```
