```
prox(f::PiecewiseQuadratic, u::Float64[, ρ::Float64=1.0]; use_quadratic::Bool=true)
```

Return the proximal operator of `f`, `ρ` evaluated at `u`.

# Note: The proximal operator of `f`, `rho` is denoted:

$$
prox_{f, rho}(u) = argmin_{x ∈ dom(f)} f(x) + (rho / 2)||x - u||_2^2
$$

See Section 6.2 of [arXiv:2103.05455](https://arxiv.org/abs/2103.05455) for more information.
