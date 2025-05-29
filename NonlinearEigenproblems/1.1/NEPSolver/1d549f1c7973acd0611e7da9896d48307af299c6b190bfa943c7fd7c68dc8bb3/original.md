```
rfi_b(nep,nept,[λ=0,][errmeasure,][tol=eps()*100,][maxit=100,][v=randn,][u=randn,][logger=0,][linsolvecreator=DefaultLinSolverCreator(),])
```

This is an implementation of the two-sided Rayleigh functional Iteration(RFI)-Bordered version to compute an eigentriplet of the problem specified by `nep`. This method requires the transpose of the NEP, specified in `nept`. `λ`, `u` and `v` are initial guesses for the eigenvalue, the right eigenvector and the left eigenvector respectively. See [`augnewton`](@ref) for other parameters.

# Example

```julia-repl
julia> nep=nep_gallery("dep0");
julia> nept=DEP([nep.A[1]',nep.A[2]'])
julia> λ,v,u=rfi_b(nep,nept,v=ones(ComplexF64,size(nep,1)))
julia> compute_resnorm(nep,λ,v) # v is a right eigenvector
5.343670589284583e-15
```

# Reference

  * Algorithm 5 in  Schreiber, Nonlinear Eigenvalue Problems: Newton-type Methods and Nonlinear Rayleigh Functionals, PhD thesis, TU Berlin, 2008.
