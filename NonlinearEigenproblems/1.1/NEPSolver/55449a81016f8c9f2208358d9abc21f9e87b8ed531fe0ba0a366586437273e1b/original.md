```
function nlar([eltype],nep::ProjectableNEP,[orthmethod=ModifiedGramSchmidt()],[neigs=10],[errmeasure],[tol=eps(real(T))*100],[maxit=100],[0=0],[v=randn(T,size(nep,1))],[logger=0],[linsolvercreator=DefaultLinSolverCreator()],[R=0.01],[eigval_sorter=residual_eigval_sorter],[qrfact_orth=false],[max_subspace=100],[num_restart_ritz_vecs=8],[inner_solver_method=DefaultInnerSolver(),][inner_logger=0])
```

The function implements the Nonlinear Arnoldi method, which finds `neigs` eigenpairs (or throws a `NoConvergenceException`) by projecting the problem to a subspace that is expanded in the course  of the algorithm. The basis is orthogonalized either by using the QR method if `qrfact_orth` is `true` or else by an orthogonalization method `orthmethod`). This entails solving a smaller projected problem using a method specified by `inner_solver_method`. The logging of the inner solvers are descided by `inner_logger`, which works in the same way as `logger`. (`λ`,`v`) is the initial guess for the eigenpair. `linsolvercreator` specifies how the linear system is created and solved. `R` is a parameter used by the function specified by `eigval_sorter` to reject those ritz values that are within a distance `R` from any of the converged eigenvalues, so that repeated convergence to the same eigenpair can be avoided. `max_subspace` is the maximum allowable size of the basis befor the algorithm restarts using a basis made of `num_restart_ritz_vecs` ritz vectors and the eigenvectors that the algorithm has converged to.

See [`augnewton`](@ref) for other parameters.

# Example

```julia-repl
julia> nep=nep_gallery("dep0_tridiag");
julia> λ,v=nlar(nep,tol=1e-7,neigs=1,maxit=100,v=ones(size(nep,1)));
julia> norm(compute_Mlincomb(nep,λ[1],v))
8.00192341259751e-7
```

# References

  * H. Voss, An Arnoldi method for nonlinear eigenvalue problems. BIT. Numer. Math. 44: 387-401, 2004.
