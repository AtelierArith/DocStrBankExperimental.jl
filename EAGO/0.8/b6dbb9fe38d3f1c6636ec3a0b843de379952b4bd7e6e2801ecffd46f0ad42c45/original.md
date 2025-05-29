```julia
mutable struct Optimizer{Q, S, T} <: MathOptInterface.AbstractOptimizer
```

The highest level optimizer object used by EAGO to solve problems during the optimization routine. Additional options and temporary storage are located in the `_global_optimizer::GlobalOptimizer{Q,S,T}` field. Parameters which are expected to be constant over the entire solve are stored in the `_parameters::EAGOParameters` field.  Some user-facing keywords not in the `EAGOParameters` field include:

  * `relaxed_optimizer::MOI.AbstractOptimizer`: An instance of the optimizer used to solve    the relaxed subproblems (default = `Cbc.Optimizer()`). Located in `subsolver_block::SubSolvers{Q,S,T}`.
  * `upper_optimizer::MOI.AbstractOptimizer`: Optimizer used to solve upper bounding problems    (default = `Ipopt.Optimizer()`). Located in `subsolver_block::SubSolvers{Q,S,T}`.
  * `ext::ExtensionType`: Holds an instance of a subtype of `EAGO.ExtensionType`, used to define   new custom subroutines (default = `DefaultExt()`). Located in `subsolver_block::SubSolvers{Q,S,T}`.
  * `enable_optimize_hook::Bool`: Specifies that the user-defined `optimize_hook!` function should   be called rather than use the standard EAGO optimization routines. Located in `Optimizer`   and `_global_optimizer::GlobalOptimizer{Q,S,T}`.
  * `obbt_variable_values::Vector{Bool}`: Variables to perform OBBT on (default: all variables in nonlinear   expressions). Located in `_global_optimizer::GlobalOptimizer{Q,S,T}`.

Descriptions of all `Optimizer` fields available in extended help.

# Extended Help

  * `subsolver_block::EAGO.SubSolvers{Q, S, T} where {Q, S, T}`: Holds definitions of the relaxed and upper optimizers, as well as any user-defined extension types
  * `enable_optimize_hook::Bool`: Specifies that the optimize_hook! function should be called rather than throw the     problem to the standard routine
  * `ext::Union{Nothing, T} where T`: (Deprecated, use `subsolver_block` instead) Storage for custom extension types
  * `_auxiliary_variable_info::Union{Nothing, EAGO._AuxVarData}`: Information on any auxiliary variables
  * `_global_optimizer::EAGO.GlobalOptimizer{Q, S, T} where {Q, S, T}`: Additional options and temporary storage for solving optimization problems
  * `_input_problem::EAGO.InputProblem`: Expressions and constraints added to the EAGO model (not directly     used for relaxations)
  * `_working_problem::EAGO.ParsedProblem`: Expressions and problem descriptions that EAGO uses to formulate     relaxed problems
  * `_parameters::EAGO.EAGOParameters`: Parameters that do not change during a global solve
  * `_optimizer_attributes_set::Vector{MathOptInterface.AbstractOptimizerAttribute}`: Set of optimizer attributes
  * `_termination_status_code::MathOptInterface.TerminationStatusCode`: The MathOptInterface-compliant completion status code
  * `_result_status_code::MathOptInterface.ResultStatusCode`: Value indicating the feasibility status of the result
  * `_run_time::Float64`: Optimization run time
  * `_objective_value::Float64`: The objective value of the primal solution
  * `_objective_bound::Float64`: The best-known bound on the optimal objective value
  * `_relative_gap::Float64`: The gap between the upper and lower bound, relative to the bound with the larger magnitude
  * `_iteration_count::Int64`: The number of iterations the branch-and-bound algorithm has completed
  * `_node_count::Int64`: The number of nodes in the stack
