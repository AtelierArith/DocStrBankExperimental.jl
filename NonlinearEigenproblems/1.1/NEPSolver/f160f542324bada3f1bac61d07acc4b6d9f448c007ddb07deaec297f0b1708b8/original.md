```
λv,V,U=infbilanczos([eltype],nep, nept,[linsolvecreator,][linsolvertcreator,][v,][u,][σ,][γ,][tol,][neigs,][errmeasure,][logger,][maxit,][check_error_every])
```

Executes the Infinite Bi-Lanczos method on the problem defined by `nep::NEP` and `nept::NEP`. `nep:NEP` is the original nonlinear eigenvalue problem and `nept::NEP` is its (hermitian) transpose: $M(λ^*)^H$.  `v` and `u` are starting vectors, `σ` is the shift and `γ` the scaling. The iteration is continued until `neigs` Ritz pairs have converged. This function throws a `NoConvergenceException` if the wanted eigenpairs are not computed after `maxit` iterations. However, if `neigs` is set to `Inf` the iteration is continued until `maxit` iterations without an error being thrown. See [`augnewton`](@ref) for other parameters.

# Example:

```julia-repl
julia> nep=nep_gallery("dep0");
julia> A=get_Av(nep); fv=get_fv(nep);
julia> At=[copy(A[1]'),copy(A[2]'),copy(A[3]')]
julia> nept=SPMF_NEP(At,fv); # Create the transposed NEP
julia> λv,V=infbilanczos(nep,nept,neigs=3,v=ones(size(nep,1)))
julia> norm(compute_Mlincomb(nep,λv[1],V[:,1]))
9.907299130783851e-15
```

# References:

  * The infinite bi-Lanczos method for nonlinear eigenvalue problems, S. W. Gaaf and E. Jarlebring, SIAM J. Sci. Comput. 39:S898-S919, 2017, [preprint](https://arxiv.org/abs/1607.03454)
