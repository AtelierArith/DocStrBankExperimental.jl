```
struct RichardsonSmoother{A} <: LinearSolver
  M     :: A
  niter :: Int64
  ω     :: Float64
end
```

Iterative Richardson smoother. Given a solution `x` and a residual `r`, performs `niter` Richardson iterations with damping parameter `ω` using the linear solver `M`.  A Richardson iteration is given by:

```
dx = ω * inv(M) * r
x  = x + dx
r  = r - A * dx
```

Updates both the solution `x` and the residual `r` in place.
