```
jd_effenberger([eltype]], nep::ProjectableNEP; [maxit=100], [neigs=1], [inner_solver_method=DefaultInnerSolver()], [orthmethod=DGKS()], [linsolvercreator=DefaultLinSolverCreator()], [tol=eps(real(T))*100], [λ=zero(T)], [v = rand(T,size(nep,1))], [target=zero(T)],  [logger=0], [inner_logger=0])
```

The function computes eigenvalues using the Jacobi-Davidson method, which is a projection method. Repreated eigenvalues are avoided by using deflation, as presented in the reference by Effenberger. The projected problems are solved using a solver spcified through the type `inner_solver_method`. The logging of the inner solvers are descided by `inner_logger`, which works in the same way as `logger`. For numerical stability the basis is kept orthogonal, and the method for orthogonalization is specified by `orthmethod`, see the package `IterativeSolvers.jl`. The function tries to compute `neigs` number of eigenvalues, and throws a `NoConvergenceException` if it cannot. The value `λ` and the vector `v` are initial guesses for an eigenpair. `linsolvercreator` is a function which specifies how the linear system is created and solved. The `target` is the center around which eiganvalues are computed. For further specifications on the `deflation_mode`, see the function `deflate_eigpair`.

See [`augnewton`](@ref) for other parameters.

# Example

```julia-repl
julia> nep=nep_gallery("dep0",100);
julia> λ,v=jd_effenberger(nep,maxit=30,v=ones(size(nep,1)),λ=0);
julia> norm(compute_Mlincomb(nep,λ[1],v[:,1]))
9.577305772525487e-15
```

# References

  * C. Effenberger, Robust successive computation of eigenpairs for nonlinear eigenvalue problems. SIAM J. Matrix Anal. Appl. 34, 3 (2013), pp. 1231-1256.

See also

  * T. Betcke and H. Voss, A Jacobi-Davidson-type projection method for nonlinear eigenvalue problems. Future Gener. Comput. Syst. 20, 3 (2004), pp. 363-372.
  * H. Voss, A Jacobi–Davidson method for nonlinear eigenproblems. In: International Conference on Computational Science. Springer, Berlin, Heidelberg, 2004. pp. 34-41.
