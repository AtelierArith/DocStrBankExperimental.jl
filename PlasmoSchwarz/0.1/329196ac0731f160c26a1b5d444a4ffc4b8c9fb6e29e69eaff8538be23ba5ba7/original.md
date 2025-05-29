```
SchwarzAlgorithm{GT<:Plasmo.AbstractOptiGraph}
```

Represents a Schwarz-based optimization algorithm applied to a partitioned graph.

Fields:

  * `graph::GT`: The global optimization graph passed to the algorithm.
  * `subproblems::Vector{GT}`: A list of subgraphs representing the (expanded) subproblems.
  * `element_subproblem_map::Dict{Plasmo.OptiElement,GT}`: Maps elements in the graph to their associated subproblems.
  * `objective_func::Plasmo.AbstractJuMPScalar`: The global objective function for the graph.
  * `options::Options`: Configuration options for the algorithm.
  * `initialized::Bool`: Whether the algorithm has been initialized.
  * `status::MOI.TerminationStatusCode`: The current status of the algorithm.
  * `err_pr::Union{Nothing,Float64}`: Current primal error.
  * `err_du::Union{Nothing,Float64}`: Current dual error.
  * `objective_value::Union{Nothing,Float64}`: Current objective value.
  * `iteration::Int64`: Current iteration count.
  * `primal_error_iters::Vector{Float64}`: History of primal errors per iteration.
  * `dual_error_iters::Vector{Float64}`: History of dual errors per iteration.
  * `objective_iters::Vector{Float64}`: History of objective values per iteration.
  * `solve_time::Float64`: Total solve time.
  * `timers::Timers`: Timers to measure performance metrics.
