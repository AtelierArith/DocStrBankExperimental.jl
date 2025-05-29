```
gradient(coord1::AbstractVector, coord2::AbstractVector, mat::Matrix; method::Symbol=:second_order)
```

勾配の有限差分法: [:backward, :central, :forward, :second*order, :third*order]

両方の次元で勾配を計算します
