```
λ,v = resinv([eltype],nep::NEP;[errmeasure,][tol,][maxit,][λ,][v,][c,][logger,][armijo_factor=1,][armijo_max,][linsolvecreator])
```

Applies residual inverse iteration method for nonlinear eigenvalue problems. The kwarg `linsolvecreator` is a function which specifies how the linear system is created. The function calls `compute_rf` for the computation of the Rayleigh functional. See [`augnewton`](@ref) for other parameters.

# Example

The example shows how to specify if the method should run in real or complex mode (or any other `Number` type).

```julia-repl
julia> nep=nep_gallery("qdep0");
julia> λ,v=resinv(nep,λ=-2,v=ones(size(nep,1)))
julia> typeof(λ)
Complex{Float64}
julia> norm(compute_Mlincomb(nep,λ,v))
6.688224435370382e-12
julia> λ,v=resinv(Float64,nep,λ=-2,v=ones(size(nep,1)))
julia> typeof(λ)
Float64
julia> norm(compute_Mlincomb(nep,λ,v))
5.939894690000396e-12
```

# References

  * A. Neumaier, Residual inverse iteration for the nonlinear eigenvalue problem, SIAM J. Numer. Anal. 22 (1985) 914-923
