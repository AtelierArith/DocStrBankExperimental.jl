```
CMPDist(λ::Real, ν::Real)
```

Conway-Maxwell-Poisson分布のパラメータ`λ`と`ν`について、詳細は[Wikipedia](https://en.wikipedia.org/wiki/Conway%E2%80%93Maxwell%E2%80%93Poisson_distribution)を参照してください。

# 例

```julia
d = CMPDist(5, 0.7)
mean(d)
pdf(d, 1)
```
