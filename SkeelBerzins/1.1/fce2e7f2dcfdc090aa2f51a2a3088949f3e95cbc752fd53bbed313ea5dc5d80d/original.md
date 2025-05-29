```julia
struct Params
```

Structure containing all the keyword arguments for the solver [`pdepe`](@ref).

  * `solver::Symbol`: Choice of the time discretization either use `:euler` for internal implicit Euler method or `:DiffEq` for the [DifferentialEquations.jl](https://github.com/SciML/DifferentialEquations.jl) package.

  * `tstep::Union{Float64, Vector{Float64}}`: Defines a time step (either pass a `Float64` or a `Vector`) when using the implicit Euler method. When set to `tstep=Inf`, it solves the stationary version of the problem.

  * `hist::Bool`: Flag, returns with the solution, a list of 1d-array with the history from the newton solver.

  * `sparsity::Symbol`: Choice of the type of matrix (`:sparseArrays`, `:banded`) use to store the jacobian.

  * `linsolve::Union{Nothing, LinearSolve.SciMLLinearSolveAlgorithm}`: Choice of the solver for the LSE in the newton method, see [`LinearSolve.jl`](https://docs.sciml.ai/LinearSolve/stable/solvers/solvers/).

  * `maxit::Int64`: Maximum number of iterations for the Newton solver.

  * `tol::Float64`: Tolerance used for Newton method. Returns solution if $||\; u_{i+1} - u_{i} \;||_2 <$ `tol`.

  * `data::Bool`: Returns the data of the PDE problem

  * `nb_design_var::Int64`: Number of design variables for PDE Constrained Optimization
