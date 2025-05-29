```
P(mod::Model{Ny,Nx,Nc,T}, x) where {Ny,Nx,Nc,T}
```

Returns Hessian of $χ²(x)$.

## Remark

  * Can be used as preconditioner, as expected by [Optim.jl](https://github.com/JuliaNLSolvers/Optim.jl).
