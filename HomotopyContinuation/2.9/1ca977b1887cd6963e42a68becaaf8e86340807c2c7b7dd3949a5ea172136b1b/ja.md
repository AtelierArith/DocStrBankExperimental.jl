```
unique_points(vectors; metric = EuclideanNorm(), atol = 1e-14, rtol = 1e-8, kwargs...)
```

`vector`内のすべての要素を返します。ここで、2つの要素の`distance`が`max(atol, rtol * metric(0,w[i]))`以下である場合です。出力は`vectors`内の要素の順序に依存する可能性があることに注意してください。残りの`kwargs`は[`UniquePoints`](@ref)に渡すことができるものです。
