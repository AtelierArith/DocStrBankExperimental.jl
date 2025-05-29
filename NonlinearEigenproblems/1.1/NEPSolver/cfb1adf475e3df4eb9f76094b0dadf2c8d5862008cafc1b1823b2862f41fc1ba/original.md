```
iar_chebyshev(nep,[maxit=30,][σ=0,][γ=1,][linsolvecreator=DefaultLinSolverCreator(),][tolerance=eps()*10000,][neigs=6,][errmeasure,][v=rand(size(nep,1),1),][logger=0,][check_error_every=1,][orthmethod=DGKS][a=-1,][b=1,][compute_y0_method=ComputeY0ChebAuto])
```

Run the infinite Arnoldi method (Chebyshev version) on the nonlinear eigenvalue problem stored in `nep`.

The target `σ` is the center around which eiganvalues are computed. A Ritz pair `λ` and `v` is flagged a as converged (to an eigenpair) if `errmeasure` is less than `tol`. The vector `v` is the starting vector for constructing the Krylov space. The orthogonalization method, used in contructing the orthogonal basis of the Krylov space, is specified by `orthmethod`, see the package `IterativeSolvers.jl`. The iteration is continued until `neigs` Ritz pairs converge. This function throws a `NoConvergenceException` if the wanted eigenpairs are not computed after `maxit` iterations. However, if `neigs` is set to `Inf` the iteration is continued until `maxit` iterations without an error being thrown. The kwarg `compute_y0_method` specifying how the next vector of the Krylov space (in Chebyshev format) can be computed. See [`compute_y0_cheb`](@ref) in the module NEPSolver with the command `?NEPSolver.compute_y0_cheb`.

See [`augnewton`](@ref) for other parameters.

# Example

```julia-repl
julia> using NonlinearEigenproblems, LinearAlgebra
julia> nep=nep_gallery("dep0",100);
julia> v0=ones(size(nep,1));
julia> λ,v=iar_chebyshev(nep;v=v0,tol=1e-5,neigs=3);
julia> norm(compute_Mlincomb!(nep,λ[1],v[:,1])) # Is it an eigenvalue?
julia> λ    # print the computed eigenvalues
3-element Array{Complex{Float64},1}:
julia> norm(compute_Mlincomb(nep,λ[1],v[:,1]))
 0.050462487848960284 - 1.4289626573515395e-18im
 -0.07708779190301127 + 7.703053374113074e-18im
   0.1503856540695659 - 1.662582577182149e-17im
```

# References

  * Algorithm 2 in Jarlebring, Michiels Meerbergen, A linear eigenvalue algorithm for the nonlinear eigenvalue problem, Numer. Math, 2012
