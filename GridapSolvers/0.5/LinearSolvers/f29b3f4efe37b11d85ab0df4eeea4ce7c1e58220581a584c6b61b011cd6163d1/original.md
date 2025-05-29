```
struct FGMRESSolver <: LinearSolver 
  ...
end

FGMRESSolver(m,Pr;Pl=nothing,restart=false,m_add=1,maxiter=100,atol=1e-12,rtol=1.e-6,verbose=false,name="FGMRES")
```

Flexible GMRES solver, with right-preconditioner `Pr` and optional left-preconditioner `Pl`.

The solver starts by allocating a basis of size `m`. Then: 

  * If `restart=true`, the basis size is fixed and restarted every `m` iterations.
  * If `restart=false`, the basis size is allowed to increase. When full, the solver  allocates `m_add` new basis vectors at a time.
