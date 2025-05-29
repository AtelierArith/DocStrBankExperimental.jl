```
HilbertianProjection(
  problem :: PDEConstrainedFunctionals{N},
  ls_evolver :: LevelSetEvolution,
  vel_ext :: VelocityExtension,
  φ0;
  orthog = HPModifiedGramSchmidt(),
  λ=0.5, α_min=0.1, α_max=1.0, γ=0.1, γ_reinit=0.5,
  ls_max_iters = 10, ls_δ_inc = 1.1, ls_δ_dec = 0.7,
  ls_ξ = 0.0025, ls_ξ_reduce_coef = 0.1, ls_ξ_reduce_abs_tol = 0.01,
  ls_γ_min = 0.001, ls_γ_max = 0.1,
  maxiter = 1000, verbose=false, constraint_names = map(i -> Symbol("C_$i"),1:N),
  converged::Function = default_hp_converged, debug = false
) where {N}
```

Create an instance of `HilbertianProjection` with several adjustable defaults including the orthogonalisation method. By default the later is [`HPModifiedGramSchmidt`](@ref).

# Required

  * `problem::PDEConstrainedFunctionals{N}`: The objective and constraint setup.
  * `ls_evolver::LevelSetEvolution`: Solver for the evolution and reinitisation equations.
  * `vel_ext::VelocityExtension`: The velocity-extension method for extending shape sensitivities onto the computational domain.
  * `φ0`: An initial level-set function defined as a FEFunction or GridapDistributed equivilent.

# Algorithm defaults

  * `γ = 0.1`: Initial coeffient on the time step size for solving the Hamilton-Jacobi evolution equation.
  * `γ_reinit = 0.5`: Coeffient on the time step size for solving the reinitisation equation.
  * `maxiter = 1000`: Maximum number of algorithm iterations.
  * `verbose=false`: Verbosity flag.
  * `constraint_names = map(i -> Symbol("C_$i"),1:N)`: Constraint names for history output.
  * `converged::Function = default_hp_converged`: Convergence criteria.
  * `has_oscillations::Function = (ls_enabled ? (args...)->false : default_has_oscillations`: By default this is disabled when a line search in enabled.
  * `os_γ_mult = 0.5`: Decrease multiplier for `γ` when `has_oscillations` returns true
  * `debug = false`: Debug flag.
  * `α_min ∈ [0,1] = 0.1`: Controls lower bound on on the projected objective descent coefficent. `α_min = 1` ignores the objective function and instead solves a constraint satisfaction problem.
  * `α_max ∈ [0,1] = 1.0`: Controls the upper bound on the projected objective descent coeffient. Typically this shouldn't change unless wanting to approach the optimum 'slower'.
  * `λ = 0.5`: The rate of contraint decrease.

Note that in practice we usually only adjust `α_min` to control the balance between improving the objective or constraints.

# Line search defaults

  * `ls_enabled = true`: Set whether a line search is used.
  * `ls_max_iters = 10`: Maximum number of line search iterations.
  * `ls_δ_inc = 1.1`: Increase multiplier for `γ` on acceptance.
  * `ls_δ_dec = 0.7`: Decrease multiplier for `γ` on rejection.
  * `ls_ξ = 1.0`: Line search tolerance for objective reduction.
  * `ls_ξ_reduce_coef = 0.0025`: Coeffient on `ls_ξ` if constraints within tolerance (see below).
  * `ls_ξ_reduce_abs_tol = 0.01`: Tolerance on constraints to reduce `ls_ξ` via `ls_ξ_reduce_coef`.
  * `ls_γ_min = 0.001`: Minimum coeffient on the time step size for solving the HJ evolution equation.
  * `ls_γ_max = 0.1`: Maximum coeffient on the time step size for solving the HJ evolution equation.

A more concervative evolution of the boundary can be achieved by decreasing `ls_γ_max`.

!!! note
    The line search has been adjusted so that it is only enforced once the constraints are within a set tolerance. This generally leads to better optimisation histories, especially for problems where constraints are far from saturation and the objective must decrease to improve the constraints.

    This can be set to always be enfored by taking `ls_ξ = 0.0025` and `ls_ξ_reduce_coef = 0.1`.

