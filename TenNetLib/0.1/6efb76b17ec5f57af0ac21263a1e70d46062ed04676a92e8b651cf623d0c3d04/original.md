```
function fullsweep!(sysenv::StateEnvs, solver, nsite::Int, swdata::SweepData;
                    kwargs...)
```

Perform a fullsweep (left-to-right and right-to-left) by `solver`.

#### Arguments:

  * `sysenv::StateEnvs`.
  * `solver`: Solver for update. Available ones: `eig_solver` and `exp_solver`.
  * `nsite::Int` of the environment. Either `1` or `2` for one-site or two-site update  respectively.
  * `swdata::SweepData`.

#### Named arguments and their default values:

  * `time_step::Union{Float64, ComplexF64, Nothing} = nothing`: Time step for TDVP.
  * `normalize::Bool = true`: Whether to normalize after update.
  * `maxdim::Int = typemax(Int)`: Maximum bond dimension after SVD truncation.
  * `mindim::Int = 1`: Minimum bond dimension after SVD truncation.
  * `cutoff::Float64 = Float64_threshold()`: Cutoff for SVD truncation.
  * `svd_alg::String = "divide_and_conquer"`.
  * `noise::Float64 = 0.0`.
  * `reverse_step::Bool = false` if `time_step = nothing`, `true` otherwise.
  * `outputlevel::Int = 1`. If `0` prints no information, for `1` outputs after every fullsweep, if `2` prints at every update step.

#### Named arguments for `solver` and their default values:

See the documentation of KrylovKit.jl.

  * `ishermitian::Bool = true`.
  * `solver_tol::Float64 = 1E-14` if `eig_solver`, `1E-12` if `exp_solver`.
  * `solver_krylovdim::Int = 5` if `eig_solver`, `30` if `exp_solver`.
  * `solver_maxiter::Int = 2` if `eig_solver`, `100` if `exp_solver`.
  * `solver_outputlevel::Int = 0`: See `verbosity` in KrylovKit.jl.
  * `solver_eager::Bool = false` if `eig_solver`, `true` if `exp_solver`.
  * `solver_check_convergence::Bool = false` if `eig_solver`, `true` if `exp_solver`.

#### Return values:

  * `::Float64`: Change in Energy ΔE
  * `::Float64`: Change in Entropy ΔS

`swdata::SweepData` gets updated.
