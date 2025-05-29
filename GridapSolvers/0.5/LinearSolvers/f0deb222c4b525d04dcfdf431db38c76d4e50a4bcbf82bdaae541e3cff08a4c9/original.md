```
struct MINRESSolver <: LinearSolver 
  ...
end

MINRESSolver(m;Pl=nothing,maxiter=100,atol=1e-12,rtol=1.e-6,verbose=false,name="MINRES")
```

MINRES solver, with optional left preconditioners `Pl`. The preconditioner must be    symmetric and positive definite.
