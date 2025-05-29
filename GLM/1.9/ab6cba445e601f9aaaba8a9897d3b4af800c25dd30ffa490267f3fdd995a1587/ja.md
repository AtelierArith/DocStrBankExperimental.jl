```
GLM.dispersion_parameter(D)
```

分布 `D` は別の分散パラメータ ϕ を持っていますか？

`Bernoulli`、`Binomial`、および `Poisson` 分布に対しては `false` を返し、それ以外の場合は `true` を返します。

# 例

```jldoctest; setup = :(using GLM)
julia> show(GLM.dispersion_parameter(Normal()))
true
julia> show(GLM.dispersion_parameter(Bernoulli()))
false
```
