```
RegularDiscretization(n1, n2, ..., np)
```

原始幾何を各パラメトリック次元に沿って `n1×n2×...×np` 要素で定期的に離散化するためのメソッドです。各タイプの幾何に対して適切な点の数が計算され、[`RegularSampling`](@ref) に渡されます。
