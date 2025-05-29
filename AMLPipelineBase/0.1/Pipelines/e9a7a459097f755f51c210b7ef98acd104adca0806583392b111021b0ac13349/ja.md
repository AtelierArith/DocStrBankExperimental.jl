```
Pipeline(machs::Vector{<:Machine},args::Dict=Dict())
```

線形パイプラインで、`fit_transform`の結果を次の要素に渡して繰り返し呼び出します。

`fit!`と`transform!`を実装しています。
