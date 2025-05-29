```
function dmrg2(psi0::MPS, H::MPO, params::DMRGParams; kwargs...)
function dmrg2(psi0::MPS, H::CouplingModel, params::DMRGParams; kwargs...)
function dmrg2(psi0::MPS, Hs::Vector{MPO}, params::DMRGParams; kwargs...)
function dmrg2(psi0::MPS, H::MPO, Ms::Vector{MPS}, params::DMRGParams; kwargs...)
function dmrg2(psi0::MPS, Hs::Vector{MPO}, Ms::Vector{MPS}, params::DMRGParams; kwargs...)
function dmrg2(psi0::MPS, H::CouplingModel, Ms::Vector{MPS}, params::DMRGParams; kwargs...)
```

Performs two-site DMRG.

#### Arguments:

  * `psi0::MPS`: Initial MPS.
  * `H::MPO`, `H::CouplingModel`, `Hs::Vector{MPO}`, `Ms::Vector{MPS}`.
  * `params::DMRGParams`.

#### Named arguments and their default values:

  * `normalize::Bool = true`: Whether to normalize after update.
  * `svd_alg::String = "divide_and_conquer"`.
  * `weight::Float64 = -1.0`: Weight for the excited state DMRG. Must be set to greater than `0` for the excited state DMRG.
  * `outputlevel::Int = 1`. If `0` prints no information, for `1` outputs after every fullsweep, if `2` prints at every update step.

#### Convergence criteria:

  * `energyErrGoal`: DMRG (at a particluar stage) stops when energy difference between two consecutive sweeps falls below this threshold and DMRG moves to the next stage. `noise` must be below `Float64_threshold()` to trigger this early stopping.
  * `entropyErrGoal`: DMRG (at a particluar stage) stops when mid-chain entropy difference between two consecutive sweeps falls below this threshold and DMRG moves to the next stage. `noise` must be below `Float64_threshold()` to trigger this early stopping.

When both `energyErrGoal` and `entropyErrGoal` are given, both conditions must be satisfied to trigger this early stopping.

#### Named arguments for `eig_solver` and their default values:

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
  * `::MPS`: The state psi.
