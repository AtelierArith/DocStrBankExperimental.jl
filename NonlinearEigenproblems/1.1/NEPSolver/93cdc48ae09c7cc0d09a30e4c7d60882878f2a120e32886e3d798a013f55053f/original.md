```
tiar(nep,[maxit=30,][σ=0,][γ=1,][linsolvecreator=DefaultLinSolverCreator(),][tolerance=eps()*10000,][neigs=6,][errmeasure,][v=rand(size(nep,1),1),][logger=0,][check_error_every=1,][orthmethod=DGKS(),][proj_solve=false,][inner_solver_method=DefaultInnerSolver(),][inner_logger=0])
```

Run the tensor infinite Arnoldi method on the nonlinear eigenvalue problem stored in `nep`. This is equivalent to `iar`, but handles orthogonalization with a tensor representation.

The target `σ` is the center around which eiganvalues are computed. The value `γ` corresponds to scaling and specifying a shift and scaling is effectively the same as the transformation `λ=γs+σ` where `s` is now the eigenvalue parameter. If you want eigenvalues in a disk centered, select `σ` as the center of the disk and `γ` as the radius. The vector `v` is the starting vector for constructing the Krylov space. The orthogonalization method, used in contructing the orthogonal basis of the Krylov space, is specified by `orthmethod`, see the package `IterativeSolvers.jl`. The iteration is continued until `neigs` Ritz pairs have converged. This function throws a `NoConvergenceException` if the wanted eigenpairs are not computed after `maxit` iterations. However, if `neigs` is set to `Inf` the iteration is continued until `maxit` iterations without an error being thrown. The parameter `proj_solve` determines if the Ritz paris are extracted using the Hessenberg matrix (false), or as the solution to a projected problem (true). If true, the method is descided by `inner_solver_method`, and the logging of the inner solvers are descided by `inner_logger`, which works in the same way as `logger`.

See [`augnewton`](@ref) for other parameters.

# Example

```julia-repl
julia> using NonlinearEigenproblems, LinearAlgebra
julia> nep=nep_gallery("dep0",100);
julia> v0=ones(size(nep,1));
julia> λ,v=tiar(nep;v=v0,tol=1e-5,neigs=3);
julia> norm(compute_Mlincomb!(nep,λ[1],v[:,1])) # Is it an eigenvalue?
julia> λ    # print the computed eigenvalues
3-element Array{Complex{Float64},1}:
 0.050462487743188206 - 3.4059600538119376e-18im
 -0.07708769561361105 + 8.611006691570004e-19im
   0.1503916927814904 + 9.388210527944734e-18im
```

# References

  * Algorithm 2 in Jarlebring, Mele, Runborg, The Waveguide Eigenvalue Problem and the Tensor Infinite Arnoldi Method, SIAM J. Scient. computing, 39 (3), A1062-A1088, 2017
