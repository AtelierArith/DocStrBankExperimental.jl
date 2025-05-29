```
BendersAlgorithm
```

Optimizer object for dual dynamic programming with graphs. Currently only implemented for linear tree structures.

Attributes include the following (where noted as dictionaries, these are mappings from the Benders subproblems to the data described)

  * `graph` - Plasmo OptiGraph for appplying Benders
  * `root_object` - node or subgraph in `graph` indicating where to start the Benders algorithm
  * `is_MIP` = Boolean indicating if the problem is a MIP or not
  * `solve_order` - vector of OptiNodes in the order that they are solved by Benders
  * `solve_order_dict` - dictionary mapping to a vector of all the "next objects" for a given object
  * `parent_objects` - dictionary mapping to the previous subproblem
  * `max_iters` - maximum number of Benders iterations
  * `time_limit` - maximum time (seconds) allowed for running Benders
  * `tol` - (absolute) termination tolerance between upper and lower bounds
  * `current_iter` - current iteration of Benders algorithm
  * `M` - lower bound for the cost-to-go function at each iteration
  * `dual_iters` - dictionary mapping optinodes to the corresponding dual values  at each iteration; dual values come from solution of following node
  * `primal_iters` - dictionary mapping optinodes to the primal solutions of the  complicating variables on the given node
  * `phis` - dictionary mapping optinodes to the objective of the immediately following node
  * `phis_LR` - dictionary mapping optinodes to the objective of the lagrangean (used for strenghtened cuts)  relaxation of the following node; used for strengthened Benders cuts in MIPs
  * `time_forward_pass` - time spent in the forward pass (seconds)
  * `time_backward_pass` - time spent in the backward pass (seconds)
  * `time_init` - time initializing the optimizer (seconds)
  * `time_iterations` - vector of the times spent in each Iteration
  * `comp_vars` - dictionary mapping the node to a vector of its complicating variables
  * `comp_var_map` - dictionary mapping the node to a dictionary of complicating variables  mapped to their index in `comp_vars`
  * `var_copy_map` - dictionary mapping the node to a dictionary mapping the complicating  variables to their copies on the following node
  * `objective_value` - the final objective value (from upper bound)
  * `lower_bounds` - vector of lower bounds at each iteration
  * `upper_bounds` - vector of upper bounds at each iteration
  * `regularize_data` - regularization data object
  * `binary_map` - dictionary mapping the nodes to a vector of binary variables on the node
  * `integer_map` - dictionary mapping the nodes to a vector of integer variables on the node
  * `last_solutions` - dictionary mapping the nodes to a vector of the last solutions
  * `var_solution_map` - dictionary mapping the variables to their index on the `last_solutions` vector
  * `var_to_graph_map` - dictionary mapping the variables to their owning subproblem subgraph
  * `feasibility_map` - dictionary matching `solve_order` for whether a problem was feasible or not
  * `options` - solver options for Benders algorithm
  * `ext` - Dictionary for extending certain procedures
