```
canonicallink(D::Distribution)
```

分布 `D` の標準リンクを返します。これは指数族に属する必要があります。

# 例

```jldoctest; setup = :(using GLM)
julia> canonicallink(Bernoulli())
LogitLink()
```
