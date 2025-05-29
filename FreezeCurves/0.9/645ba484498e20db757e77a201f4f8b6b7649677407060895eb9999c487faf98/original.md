```
SFCCNewtonSolver <: SFCCSolver
```

Fast, specialized implementation of Newton's method with backtracking line search for resolving the energy conservation law, H = TC + Lθ. Attempts to find the root of the corresponding temperature residual: ϵ = T - (H - Lθ(T)) / C(θ(T)) and uses backtracking to avoid jumping over the solution. This prevents convergence issues that arise due to discontinuities and strong non-linearity in most common soil freeze curves.
