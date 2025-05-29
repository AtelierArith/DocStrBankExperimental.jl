```
function fullsweep!(sysenv::StateEnvsTTN, sweeppath::Vector{Int2}, solver,
                    swdata::SweepDataTTN; kwargs...)
```

Perform a fullsweep of the TTN by `solver`.

#### Arguments:

  * `sysenv::StateEnvsTTN`.
  * `sweeppath::Vector{Int2}`: The list of nodes as the path to be followed during a (half)sweep. Must have each node atleast once. For the next halfsweep the reverse path is followed.
  * `solver`: Solver for update. Currently only `eig_solver` is supported.
  * `swdata::SweepDataTTN`.

#### Named arguments and their default values:

  * `time_step::Union{Float64, ComplexF64, Nothing} = nothing`: Time step for future functionality.
  * `normalize::Bool = true`: Whether to normalize after update.
  * `maxdim::Int = typemax(Int)`: Maximum bond dimension after SVD truncation.
  * `mindim::Int = 1`: Minimum bond dimension after SVD truncation.
  * `cutoff::Float64 = Float64_threshold()`: Cutoff for SVD truncation.
  * `svd_alg::String = "divide_and_conquer"`.
  * `noise::Float64 = 0.0`.
  * `expand_dim::Int = 0` if `noise == 0` else `20`. Dimension to be expanded (on top of `maxdim`) during subspace expansion.
  * `max_expand_dim::Int = 2 * expand_dim`. maximum dimension to be expanded during subspace expansion.
  * `expand_numiter::Int = 4`. Number of iteration for subspace expansion. Should be greater than 1.
  * `linkwise_maxdim::Union{Nothing, Dict{LinkTypeTTN, Int}} = nothing`. Specifies maximum bond dimension of a particular link.
  * `outputlevel::Int = 1`. If `0` prints no information, for `1` outputs after every fullsweep, if `2` prints at every update step.

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

  * `::Float64`: Change in Energy ΔE

`swdata::SweepDataTTN` gets updated.
