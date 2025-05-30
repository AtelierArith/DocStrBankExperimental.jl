```
getlogbasemeasure(::Type{<:Distribution}, [ conditioner ])
```

`Distributions.jl` パッケージの分布タイプに特に定義された `getbasemeasure` の一般的なバージョンです。条件付き指数族分布には、追加の `conditioner` 引数が必要です。基準測度の対数を計算するだけです。
