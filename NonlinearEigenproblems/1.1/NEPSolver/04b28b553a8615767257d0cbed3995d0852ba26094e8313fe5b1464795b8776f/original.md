```
ilan(nep,[maxit=30,][σ=0,][γ=1,][linsolvecreator=DefaultLinSolverCreator(),][tolerance=eps()*10000,][neigs=6,][errmeasure,][v=rand(size(nep,1),1),][logger=0,][check_error_every=30,][orthmethod=DGKS])
```

Run the infinite Lanczos method on the symmetric nonlinear eigenvalue problem stored in `nep`. The current implementation supports only `nep`s in `SPMF` format.

The target `σ` is the center around which eiganvalues are computed. The kwarg `errmeasure` is a function handle which can be used to specify how the error is measured to be used in termination (default is absolute residual norm). A Ritz pair `λ` and `v` is flagged a as converged (to an eigenpair) if `errmeasure` is less than `tol`. The vector `v` is the starting vector for constructing the Krylov space. The orthogonalization method, used in contructing the orthogonal basis of the Krylov space, is specified by `orthmethod`, see the package `IterativeSolvers.jl`. The iteration is continued until `neigs` Ritz pairs have converged. This function throws a `NoConvergenceException` if the wanted eigenpairs are not computed after `maxit` iterations. However, if `neigs` is set to `Inf` the iteration is continued until `maxit` iterations without an error being thrown.

See [`augnewton`](@ref) for other parameters.

# Example

```julia-repl
julia> using NonlinearEigenproblems, LinearAlgebra
julia> nep=nep_gallery("dep_symm_double",10);
julia> v0=ones(size(nep,1));
julia> λ,v=ilan(nep;v=v0,tol=1e-5,neigs=3);
julia> norm(compute_Mlincomb!(nep,λ[1],v[:,1])) # Is it an eigenvalue?
julia> λ    # print the computed eigenvalues
3-element Array{Complex{Float64},1}:
  0.03409997385842267 - 1.425205509434608e-19im
 -0.03100798730589012 + 5.66201058098364e-20im
  -0.0367653644764646 - 1.607494907684445e-19im
```

# References

  * Algorithm 2 in Mele, The infinite Lanczos method for symmetric nonlinear eigenvalue problems, https://arxiv.org/abs/1812.07557, 2018
