```
function update_position!(sysenv::StateEnvsTTN, solver, node::Int2;
                          time_step::Union{Float64, ComplexF64, Nothing},
                          normalize::Bool,
                          maxdim::Int,
                          mindim::Int,
                          cutoff::Float64,
                          svd_alg::String,
                          kwargs...)
```

Moves the orthogonality center to `pos` and update StateEnvsTTN at position `pos` by `solver`.

#### Arguments:

  * `sysenv::StateEnvsTTN`
  * `solver`: Solver for update. Currently only `eig_solver` is supported.
  * `pos::Int`: Position of the node to be updated.

#### Named arguments and their default values:

  * `time_step::Union{Float64, ComplexF64, Nothing} = nothing`: Time step for future functionality.
  * `normalize::Bool = true`: Whether to normalize after update.
  * `maxdim::Int = typemax(Int)`: Maximum bond dimension after SVD truncation.
  * `mindim::Int = 1`: Minimum bond dimension after SVD truncation.
  * `cutoff::Float64 = Float64_threshold()`: Cutoff for SVD truncation.
  * `svd_alg::String = "divide_and_conquer"`.

#### Named arguments for `solver` and their default values:

See the documentation of KrylovKit.jl.

  * `ishermitian::Bool = true`.
  * `solver_tol::Float64 = 1E-14`.
  * `solver_krylovdim::Int = 5`.
  * `solver_maxiter::Int = 2`.
  * `solver_outputlevel::Int = 0`: See `verbosity` in KrylovKit.jl.
  * `solver_eager::Bool = false`.
  * `solver_check_convergence::Bool = false`.

#### Return values:

  * `::Float64`: Energy.
