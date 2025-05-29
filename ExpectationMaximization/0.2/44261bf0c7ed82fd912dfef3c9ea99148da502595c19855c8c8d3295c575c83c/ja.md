```
fit_mle(g::Product, x::AbstractMatrix)
fit_mle(g::Product, x::AbstractMatrix, γ::AbstractVector)
```

多変量Product分布`g`の`fit_mle`は、`g`の各コンポーネントの`fit_mle`の`product_distribution`です。Productは次のバージョンの`Distribution.jl`で非推奨となる予定です。代わりに`VectorOfUnivariateDistribution`型を使用してください。
