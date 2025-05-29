```
CovarianceFunction(d, cov)
```

次元 `d` の共分散関数と共分散構造 `cov`。

# 例

```jldoctest
julia> CovarianceFunction(1, Exponential(0.1))
1次元指数共分散関数 (λ=0.1, σ=1.0, p=2.0)

julia> CovarianceFunction(2, Matern(0.1, 1.0))
2次元マテーン共分散関数 (λ=0.1, ν=1.0, σ=1.0, p=2.0)

```
