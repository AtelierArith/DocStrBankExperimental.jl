```
prox(f::PiecewiseQuadratic, u::Float64[, ρ::Float64=1.0]; use_quadratic::Bool=true)
```

`f`の近接作用素、`ρ`が`u`で評価されます。

# 注: `f`の近接作用素、`rho`は次のように表されます:

$$
prox_{f, rho}(u) = argmin_{x ∈ dom(f)} f(x) + (rho / 2)||x - u||_2^2
$$

詳細については、[arXiv:2103.05455](https://arxiv.org/abs/2103.05455)のセクション6.2を参照してください。
