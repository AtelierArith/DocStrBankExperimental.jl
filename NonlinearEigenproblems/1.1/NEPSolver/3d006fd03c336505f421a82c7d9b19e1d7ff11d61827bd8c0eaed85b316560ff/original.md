```
λ,v = implicitdet([eltype],nep::NEP;[errmeasure,][tol,][maxit,][λ,][v,][c,][logger])
```

This function implements the Implicit determinant method as formulated Algorithm 4.3 in the reference. The method applies Newton-Raphson to the equation $det(M(λ))/det(G(λ)) = 0$, where $G(λ)$ is a saddle point matrix with $M(λ)$ in the (1,1) block. The (2,1) and (1,2) blocks of $G(λ)$ are set to $c^H$ and $c$ respectively. Note that $G(λ)$ can be non-singular even when $M(λ)$ is singular. See reference for more information. See [`augnewton`](@ref) for other parameters.

# Example

```julia-repl
julia> nep=nep_gallery("pep0")
julia> λ,v=implicitdet(nep,v=ones(size(nep,1)));
julia> norm(compute_Mlincomb(nep,λ,v))/norm(v)
2.566371972986362e-14
```

# References

  * Spence, A., & Poulton, C. (2005). Photonic band structure calculations using nonlinear eigenvalue techniques, J. Comput. Phys., 204 (2005), pp. 65–8
  * Güttel, S., & Tisseur, F. (2017). The nonlinear eigenvalue problem. Acta Numerica, 26, 1-94. doi:10.1017/S0962492917000034
