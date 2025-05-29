```
function optimize(psi0::TTN, H::CouplingModel,
                  params::OptimizeParamsTTN,
                  sweeppath::Vector{Int2};
                  kwargs...)

function optimize(psi0::TTN, H::CouplingModel, Ms::Vector{TTN},
                  params::OptimizeParamsTTN,
                  sweeppath::Vector{Int2};
                  kwargs...)
```

Performs optimization of the TTN.

#### Arguments:

  * `psi0::TTN`: Initial TTN.
  * `H::CouplingModel`, `Ms::Vector{MPS}`.
  * `params::OptimizationParamsTTN`.
  * `sweeppath::Vector{Int2}`: The path to be followed during optimization sweep. A vector that must contain all the nodes atleast once.

#### Named arguments and their default values:

  * `normalize::Bool = true`: Whether to normalize after update.
  * `svd_alg::String = "divide_and_conquer"`.
  * `weight::Float64 = -1.0`: Weight for the excited state calculation. Must be set to greater than `0` for the excited state optimization.
  * `outputlevel::Int = 1`. If `0` prints no information, for `1` outputs after every fullsweep, if `2` prints at every update step.

#### Convergence criteria:

  * `energyErrGoal`: Optimization (at a particluar stage) stops when energy difference between two consecutive sweeps falls below this threshold and the optimzation moves to the next stage. `noise` must be below `Float64_threshold()` to trigger this early stopping.

#### Named arguments for `eig_solver` and their default values:

See documentation of KrylovKit.jl.

  * `ishermitian::Bool = true`
  * `solver_tol::Float64 = 1E-14`.
  * `solver_krylovdim::Int = 3`.
  * `solver_maxiter::Int = 1`.
  * `solver_outputlevel::Int = 0`: See `verbosity` in KrylovKit.jl.
  * `solver_eager::Bool = false`.
  * `solver_check_convergence::Bool = false`.

#### Return values:

  * `::Float64`: Energy.
  * `::TTN`: The state psi.
