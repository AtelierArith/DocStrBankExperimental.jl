```
function dynamic_fullsweep!(sysenv::StateEnvs, solver, swdata::SweepData;
                            kwargs...)
```

Perform a dynamic fullsweep (left-to-right and right-to-left) by `solver`. The very first sweep, as dictated by `swdata.sweepcount=0`, Global Subspace Expansion (see below) is performed followed by a pure one-site sweep if `typeof(sysenv) == StateEnvs{ProjMPO}`, else performs a full two-site sweep. At each bond, if the lowest eigenvalue is below `eigthreshold` or the bond dimension at that bond has reached `maxdim` at a particular halfsweep, performs single-site update across that bond in the subsequent halfsweep, otherwise performs two-site update.

#### Arguments:

  * `sysenv::StateEnvs`.
  * `solver`: Solver for update. Available ones: `eig_solver` and `exp_solver`.
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
  * `eigthreshold::Float64 = 1E-12`.
  * `extendat::Union{Nothing, Int} = nothing`: If specified, at every `extendat`th sweep, Global Subspace Expansion is performed followed by a pure one-site sweep if `typeof(sysenv) == StateEnvs{ProjMPO}`, else performs a full two-site sweep.

#### Named arguments for `solver` and their default values:

See the documentation of KrylovKit.jl.

  * `ishermitian::Bool = true`.
  * `solver_tol::Float64 = 1E-14` if `eig_solver`, `1E-12` if `exp_solver`.
  * `solver_krylovdim::Int = 3` if `eig_solver`, `30` if `exp_solver`.
  * `solver_maxiter::Int = 1` if `eig_solver`, `100` if `exp_solver`.
  * `solver_outputlevel::Int = 0`: See `verbosity` in KrylovKit.jl.
  * `solver_eager::Bool = false` if `eig_solver`, `true` if `exp_solver`.
  * `solver_check_convergence::Bool = false` if `eig_solver`, `true` if `exp_solver`.

#### Arguments for Global Subspace Expansion and their default values:

  * `extension_krylovdim::Int = 3`: Number of Krylov vectors used for GSE.
  * `extension_applyH_cutoff::Float64 = 0.0`: Cutoff for the application of the MPO to the MPS.
  * `extension_applyH_maxdim::Int = maxlinkdim(psi) + 1`: Maximum bond/link dimension for the application of the MPO to the MPS.
  * `extension_cutoff::Float64 = 1E-10`: Cutoff for the basis extension step in GSE.

#### Return values:

  * `::Float64`: Change in Energy ΔE
  * `::Float64`: Change in Entropy ΔS

`swdata::SweepData` gets updated.
