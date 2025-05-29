```
struct CGSolver <: LinearSolver
  ...
end

CGSolver(Pl;maxiter=1000,atol=1e-12,rtol=1.e-6,flexible=false,verbose=0,name="CG")
```

Left-Preconditioned Conjugate Gradient solver.
