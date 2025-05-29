```
(S,X)=blocknewton(nep [S,] [X,] [errmeasure,] [tol,] [maxit,] [armijo_factor,] [armijo_max,] [logger])
```

Applies the block Newton method to `nep::AbstractSPMF`. The method computes an invariant pair `(S,X)` using the block Newton approach of Kressner. The variables `S`,`X` correspond to starting approximations. The function `errmeasure` shoule be defined for errmeasure(S,X) and meausures the error in the pair `(S,X)`. See [`augnewton`](@ref) for other parameters.

# Example

The example shows that `compute_MM()` becomes zero when a solution has been computed.

```julia-repl
julia> nep=nep_gallery("dep0",3);
julia> (S,X)= blocknewton(nep)
julia> compute_MM(nep,S,X)
3×2 Array{Complex{Float64},2}:
 -1.11022e-16+0.0im  1.11022e-16+0.0im
          0.0+0.0im          0.0+0.0im
  1.38778e-17+0.0im  2.77556e-17+0.0im
```

This example solves the `gun` problem from the Berlin-Manchester collection

```julia-repl
julia> using NonlinearEigenproblems.Gallery
julia> nep=nep_gallery("nlevp_native_gun");
julia> II=[1.0 0; 0 1]; S=150^2*II; V=[II;zeros(size(nep,1)-2,2)];
julia> (Z,X)=blocknewton(nep,S=S,X=V,logger=1,armijo_factor=0.5,maxit=20)
Iteration 1: Error: 6.081316e+03
Iteration 2: Error: 1.701970e-02 Armijo scaling=0.031250
Iteration 3: Error: 1.814887e-02 Armijo scaling=0.250000
...
Iteration 13: Error: 6.257442e-09
Iteration 14: Error: 2.525942e-15
```

# References

  * D. Kressner A block Newton method for nonlinear eigenvalue problems, Numer. Math., 114 (2) (2009), pp. 355-372
