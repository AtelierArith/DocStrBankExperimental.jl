```
update_position!(sysenv::StateEnvs, solver, pos::Int, nsite::Int, ortho::String; kwargs...)
```

Updates StateEnvs at position `pos` by `solver`.

#### Arguments:

  * `sysenv::StateEnvs`
  * `solver`: Solver for update. Available ones: `eig_solver` and `exp_solver`.
  * `pos::Int`: Position of the bond (`nsite=2`) or site (`nsite=1`).
  * `nsite` of the environment. Either `1` or `2` for one-site or two-site update respectively.
  * `ortho::String`: Direction of the sweep. Either `"left"` or `"right"`.

#### Named arguments and their default values:

  * `time_step::Union{Float64, ComplexF64, Nothing} = nothing`: Time step for TDVP.
  * `normalize::Bool = true`: Whether to normalize after update.
  * `maxdim::Int = typemax(Int)`: Maximum bond dimension after SVD truncation.
  * `mindim::Int = 1`: Minimum bond dimension after SVD truncation.
  * `cutoff::Float64 = Float64_threshold()`: Cutoff for SVD truncation.
  * `svd_alg::String = "divide_and_conquer"`.
  * `noise::Float64 = 0.0`.
  * `reverse_step::Bool = false` if `time_step = nothing`, `true` otherwise.

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

  * `::Float64`: Energy.
  * `::Float64`: Truncation Error.
  * `::Vector{Float64}`: SVD spectrum.
