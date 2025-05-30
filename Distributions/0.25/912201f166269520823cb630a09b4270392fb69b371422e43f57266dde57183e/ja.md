```
cgf(d::UnivariateDistribution, t)
```

分布 `d` の [累積生成関数](https://en.wikipedia.org/wiki/Cumulant) を `t` で評価します。

累積生成関数は [モーメント生成関数](https://en.wikipedia.org/wiki/Moment-generating_function) の対数です: `cgf = log ∘ mgf`。ただし、実際には右辺にオーバーフローの問題があるかもしれません。

また [`mgf`](@ref) も参照してください。
