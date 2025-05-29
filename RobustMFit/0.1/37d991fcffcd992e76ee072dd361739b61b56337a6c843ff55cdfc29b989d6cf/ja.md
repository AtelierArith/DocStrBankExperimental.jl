```
Dagum(a::Real, b::Real, p::Real)
```

パラメータ `a`、`b`、`p` を持つダグム分布、詳細は [Wikipedia](https://en.wikipedia.org/wiki/Dagum_distribution)

# 例

```julia
d = Dagum(2, 1, 1)
mean(d)
pdf(d, 1)
```
