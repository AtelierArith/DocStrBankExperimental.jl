```
symplectic_integrate(x₀, p₀, Λ, U, δUδx, N=50, ϵ=0.1, progress=false)
```

Do a symplectic integration of the potential energy `U` (with gradient `δUδx`) starting from point `x₀` with momentum `p₀` and mass matrix `Λ`. The number of steps is `N` and the step size `ϵ`. 

Returns `ΔH, xᵢ, pᵢ` corresponding to change in Hamiltonian, and final position and momenta. If `history_keys` is specified a history of requested variables throughout each step is also returned. 
