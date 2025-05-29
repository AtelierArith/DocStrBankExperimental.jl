```
location(X; c=9, M=nothing)
location(X::AbstractArray; dims=:, kwargs...)
```

バイウェイト位置を計算します。これは、位置のロバストな測定値です。

$$
\hat{y} = \frac{\sum_{u_i^2 \le 1}{y_i(1 - u_i^2)^2}}{\sum_{u_i^2 \le 1}{(1 - u_i^2)^2}}
$$

# 例

```jldoctest
julia> X = 10 .* randn(rng, 1000) .+ 50;


julia> location(X)
49.98008021468018
```

## 反復的な精緻化

中央値を手動で渡すことによって、位置推定を反復的に精緻化できます。次のように-

```jldoctest
X = 10 .* randn(rng, 1000) .+ 50
let ystar, ystar_old
    ystar = ystar_old = location(X)
    tol = 1e-6
    maxiter = 10
    for _ = 1:maxiter
        ystar = location(X; M=ystar_old)
        isapprox(ystar_old, ystar; atol=tol) && break
        ystar_old = ystar
    end
    ystar
end

# 出力

49.991666155308145
```

# 参考文献

1. [NIST: biweight location](https://www.itl.nist.gov/div898/software/dataplot/refman2/auxillar/biwloc.htm)

```
