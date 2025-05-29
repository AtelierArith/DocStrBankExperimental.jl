```julia
struct NewtonPar{T, L<:BifurcationKit.AbstractLinearSolver, E<:BifurcationKit.AbstractEigenSolver}
```

Returns a variable containing parameters to affect the `newton` algorithm when solving `F(x) = 0`.

# Arguments (with default values):

  * `tol::Any`: absolute tolerance for `F(x)` Default: 1.0e-12
  * `max_iterations::Int64`: number of Newton iterations Default: 25
  * `verbose::Bool`: display Newton iterations? Default: false
  * `linsolver::BifurcationKit.AbstractLinearSolver`: linear solver, must be `<: AbstractLinearSolver` Default: DefaultLS()
  * `eigsolver::BifurcationKit.AbstractEigenSolver`: eigen solver, must be `<: AbstractEigenSolver` Default: DefaultEig()
  * `linesearch::Bool`: Default: false
  * `α::Any`: Default: convert(typeof(tol), 1.0)
  * `αmin::Any`: Default: convert(typeof(tol), 0.001)

# Arguments for line search (Armijo)

  * `linesearch = false`: use line search algorithm (i.e. Newton with Armijo's rule)
  * `α = 1.0`: initial value of α (damping) parameter for line search algorithm
  * `αmin  = 0.001`: minimal value of the damping `alpha`

!!! tip "Mutating"
    For performance reasons, we decided to use an immutable structure to hold the parameters. One can use the package `Accessors.jl` to drastically simplify the mutation of different fields. See the tutorials for examples.

