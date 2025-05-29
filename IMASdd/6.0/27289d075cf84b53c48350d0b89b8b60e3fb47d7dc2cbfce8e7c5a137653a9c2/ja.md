```
gradient(coord1::AbstractVector, coord2::AbstractVector, mat::Matrix, dim::Int; method::Symbol=:second_order)
```

勾配の有限差分法: [:backward, :central, :forward, :second*order, :third*order]

最初の次元 (dim=1) または第二の次元 (dim=2) に適用できます。
