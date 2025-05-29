```
(ls::StrongWolfe)(ϕ, dϕ, ϕdϕ, alpha0, ϕ_0, dϕ_0) -> alpha, ϕalpha
```

Given `ϕ(alpha::Real)`, its derivative `dϕ`, a combined-evaluation function `ϕdϕ(alpha) -> (ϕ(alpha), dϕ(alpha))`, and an initial guess `alpha0`, identify a value of `alpha > 0` satisfying the strong Wolfe conditions.

`ϕ_0` and `dϕ_0` are the value and derivative, respectively, of `ϕ` at `alpha = 0.`

Both `alpha` and `ϕ(alpha)` are returned.
