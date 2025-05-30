```
getbasemeasure(::Type{<:Distribution}, [ conditioner ])
```

`Distributions.jl` パッケージの分布型に特に定義された `getbasemeasure` の特定のバージョンです。`ExponentialFamilyDistribution` のインスタンスを必要とせず、特定の分布型で直接呼び出すことができます。条件付き指数族分布には、追加の `conditioner` 引数が必要です。
