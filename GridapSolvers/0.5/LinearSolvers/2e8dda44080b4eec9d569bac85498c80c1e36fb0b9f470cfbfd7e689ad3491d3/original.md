```
struct GMRESSolver <: LinearSolver 
  ...
end

GMRESSolver(m;Pr=nothing,Pl=nothing,restart=false,m_add=1,maxiter=100,atol=1e-12,rtol=1.e-6,verbose=false,name="GMRES")
```

GMRES solver, with optional right and left preconditioners `Pr` and `Pl`.

The solver starts by allocating a basis of size `m`. Then: 

  * If `restart=true`, the basis size is fixed and restarted every `m` iterations.
  * If `restart=false`, the basis size is allowed to increase. When full, the solver  allocates `m_add` new basis vectors.
