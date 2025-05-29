```
ITP(; k1::Real = 0.007, k2::Real = 1.5, n0::Int = 10)
```

ITP (Interpolate Truncate & Project)

Use the [ITP method](https://en.wikipedia.org/wiki/ITP_method) to find a root of a bracketed function, with a convergence rate between 1 and 1.62.

This method was introduced in the paper "An Enhancement of the Bisection Method Average Performance Preserving Minmax Optimality" (https://doi.org/10.1145/3423597) by I. F. D. Oliveira and R. H. C. Takahashi.

### Tuning Parameters

The following keyword parameters are accepted.

  * `n₀::Int = 10`, the 'slack'. Must not be negative. When n₀ = 0 the worst-case is identical to that of bisection, but increasing n₀ provides greater opportunity for superlinearity.
  * `scaled_κ₁::Float64 = 0.2`. Must not be negative. The recommended value is `0.2`. Lower values produce tighter asymptotic behaviour, while higher values improve the steady-state behaviour when truncation is not helpful.
  * `κ₂::Real = 2`. Must lie in [1, 1+ϕ ≈ 2.62). Higher values allow for a greater convergence rate, but also make the method more succeptable to worst-case performance. In practice, κ₂=1, 2 seems to work well due to the computational simplicity, as κ₂ is used as an exponent in the method.

### Computation of κ₁

In the current implementation, we compute κ₁ = scaled_κ₁·|Δx₀|^(1 - κ₂); this allows κ₁ to adapt to the length of the interval and keep the proposed steps proportional to Δx.

### Worst Case Performance

n½ + `n₀` iterations, where n½ is the number of iterations using bisection (n½ = ⌈log2(Δx)/2`tol`⌉).

### Asymptotic Performance

If `f` is twice differentiable and the root is simple, then with `n₀` > 0 the convergence rate is √`κ₂`.
