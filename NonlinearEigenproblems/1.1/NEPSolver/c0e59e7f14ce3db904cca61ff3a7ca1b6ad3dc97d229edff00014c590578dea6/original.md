```
jd_betcke([eltype]], nep::ProjectableNEP; [neigs=1], [tol=eps(real(T))*100], [maxit=100], [λ=zero(T)], [orthmethod=DGKS],  [errmeasure], [linsolvercreator=DefaultLinSolverCreator()], [v = randn(size(nep,1))], [logger=0], [inner_logger=0], [inner_solver_method=DefaultInnerSolver()], [projtype=:PetrovGalerkin], [target=zero(T)])
```

The function computes eigenvalues using Jacobi-Davidson method, which is a projection method. The projected problems are solved using a solver spcified through the type `inner_solver_method`. The logging of the inner solvers are descided by `inner_logger`, which works in the same way as `logger`. For numerical stability the basis is kept orthogonal, and the method for orthogonalization is specified by `orthmethod`, see the package `IterativeSolvers.jl`. The function tries to compute `neigs` number of eigenvalues, and throws a `NoConvergenceException` if it cannot. The value `λ` and the vector `v` are initial guesses for an eigenpair. `linsolvercreator` is a function which specifies how the linear system is created and solved. The `target` is the center around which eiganvlues are computed. By default the method uses a Petrov-Galerkin framework, with a trial (left) and test (right) space, hence $W^H T(λ) V$ is the projection considered. By specifying  `projtype` to be `:Galerkin` then `W=V`.

See [`augnewton`](@ref) for other parameters.

# Example

```julia-repl
julia> nep=nep_gallery("dep0",50);
julia> λ,v=jd_betcke(nep,tol=1e-8,maxit=20);
julia> norm(compute_Mlincomb(nep,λ[1],v[:,1]))
1.9570222439914163e-10
```

# References

  * T. Betcke and H. Voss, A Jacobi-Davidson-type projection method for nonlinear eigenvalue problems. Future Gener. Comput. Syst. 20, 3 (2004), pp. 363-372.
  * H. Voss, A Jacobi–Davidson method for nonlinear eigenproblems. In: International Conference on Computational Science. Springer, Berlin, Heidelberg, 2004. pp. 34-41.

See also

  * C. Effenberger, Robust successive computation of eigenpairs for nonlinear eigenvalue problems. SIAM J. Matrix Anal. Appl. 34, 3 (2013), pp. 1231-1256.
