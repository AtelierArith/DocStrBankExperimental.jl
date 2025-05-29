```
λ,v = newton([eltype],nep::NEP;[errmeasure,][tol,][maxit,][λ,][v,][c,][logger,][armijo_factor=1,][armijo_max])
```

Applies Newton-Raphsons method on the system of nonlinear equations with `n+1` unknowns:

$$
M(λ)v=0
$$

$$
c^Hv-1=0
$$

The vector `c` is the orthogonalization vector.  If `c=0` the current approximation will be used for the orthogonalization. See [`augnewton`](@ref) for other parameters.

# Example

```julia-repl
julia> using LinearAlgebra
julia> nep=nep_gallery("dep0");
julia> λ,v=newton(nep);
julia> minimum(svdvals(compute_Mder(nep,λ)))
1.9997125567227177e-16
```

# References

  * Nichtlineare Behandlung von Eigenwertaufgaben, Z. Angew. Math. Mech. 30 (1950) 281-282.
  * A. Ruhe, Algorithms for the nonlinear eigenvalue problem, SIAM J. Numer. Anal. 10 (1973) 674-689
