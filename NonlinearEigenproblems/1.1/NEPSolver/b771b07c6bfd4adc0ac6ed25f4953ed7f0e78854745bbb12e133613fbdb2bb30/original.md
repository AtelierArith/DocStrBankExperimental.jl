```
rfi(nep,nept,[λ=0,][errmeasure,][tol=eps()*100,][maxit=100,][v=randn,][u=randn,][logger=0,][linsolvecreator=DefaultLinSolverCreator(),])
```

This is an implementation of the two-sided Rayleigh functional Iteration (RFI) to compute an eigentriplet of the problem specified by `nep`. This method requires the transpose of the NEP, specified in `nept`. `λ`, `u` and `v` are initial guesses for the eigenvalue, the right eigenvector and the left eigenvector respectively. See [`augnewton`](@ref) for other parameters.

# Example

```julia-repl
julia> nep=nep_gallery("dep0");
julia> nept=DEP([nep.A[1]',nep.A[2]'])
julia> λ,v,u=rfi(nep,nept)
julia> compute_resnorm(nep,λ,v) # v is a right eigenvector
3.0171586304599647e-16
julia> compute_resnorm(nept,λ,u) # u is a right eigenvector
7.145081514857076e-17
```

# Reference

  * Algorithm 4 in  Schreiber, Nonlinear Eigenvalue Problems: Newton-type Methods and Nonlinear Rayleigh Functionals, PhD thesis, TU Berlin, 2008.
