```
λ,v = newtonqr([eltype],nep::NEP;[errmeasure,][tol,][maxit,][λ,][v,][c,][logger])
```

This function implements the Newton-QR method as formulated in the reference. The method involves the computation of a rank-revealing QR factorization of $M(λ)$, with the idea that on convergence the the last diagonal element $R[n,n]$ of the upper-triangular matrix $R$ becomes zero as a result of $M(λ)$ becoming singular. Since the computation of a QR factorization is expensive, it is advisable to use this method for problems of small size or problems with a certain structure that makes the QR computation less expensive. See [`augnewton`](@ref) for other parameters.

# Example

```julia-repl
julia> nep=nep_gallery("pep0")
julia> λ,v=newtonqr(nep,v=ones(size(nep,1)));
julia> norm(compute_Mlincomb(nep,λ,v))/norm(v)
8.440206093655014e-15
```

# References

  * Kublanovskaya, V. N., (1970).  On an approach to the solution of the generalized latent value problem for λ-matrices, SIAM J. Numer. Anal. 7, 532–537
  * Güttel, S., & Tisseur, F. (2017). The nonlinear eigenvalue problem. Acta Numerica, 26, 1-94. doi:10.1017/S0962492917000034
