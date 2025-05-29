Creates an opaque `RoutingData` object based on the topology of the network `g` and the demands to route `k`. Calling this function may take a while, as it precomputes many things used later on, based on the type of model to use. Not all parameters are used in all cases.

Parameters that are always used (only the first three are required and positional):

  * `g` is a directed graph with annotation (hence the type `MetaDiGraph`). Each edge is supposed to have a property `capacity` giving its capacity (units are not imposed by the package, but must be consistent). Each node must have a `name` property, which will be used for generating the output.
  * `k` is another directed graph, without necessarily annotations (hence the type `AbstractSimpleGraph`).
  * `solver` is the optimization solver to use for this problem (like `CPLEX.Optimizer`).
  * `model_type` is the type of optimisation model used to compute the oblivious routing. Its type is `ModelType`.
  * `name` is an optional name for the model.

The parameters almost always apply, and may have tremendous impact on solving performance:

  * `model_simplifications` enables simplifications in the model. They do not imply any kind of approximation. Computing what parts of the model can be simplified may take more time than what the simplifications may improve the running times of the optimalisation part (especially for small networks and those with very high connexity).
  * `remove_unreachable_nodes` determines whether the nodes in the topology `g` that are isolated, i.e. those that have no neighbours, should be removed
  * `remove_unsatisfiable_demands` determines whether the demands that are not routable (i.e. there is no path in `g` from their source to their destination, the topology `g` provides no connectivity between these two nodes) should be removed.
  * `timeout`: the maximum time for the computations. `Second(0)` indicates that there is no limit. If the time limit is reached, the resulting solution will have the `MOI.TIME_LIMIT` status code with the current solution: it will have no optimality or feasibility guarantee!
  * `enable_variable_constraint_names`: whether variables and constraints should have names attached to them. Enabling this option (the default) eases the debugging of the models; disabling it improves performance, especially for large models.

Some models may use these parameters:

  * `sub_model_type` is only used by algorithms using subproblems, like oblivious routing with cutting planes. All the following parameters are reused for the subproblems: `model_simplifications`, `npaths`.
  * `npaths` is the number of shortest paths that should be computed beforehand for path-based formulations, solved with column generation or not. This number of paths is considered *for each demand*: there will be probably more than `npaths` that get generated, but never more than `npaths` times the number of demands). By default, 20 paths at most are generated for each demand. For column-generation-based formulations, this provides a starting set of columns: this set may be increased in size during the solving process. Otherwise, this is the total number of paths that will be used for solving the problem.

These parameters are only used for oblivious routing:

  * `model_all_traffic_matrices` indicates whether all traffic matrices that violate the oblivious routing constraints should be added or not, at each iteration of the master problem. (The original algorithm only adds one matrix, but adding more at a time may improve running times by reducing the total number of iterations to perform.)
  * `model_exact_opt_d` indicates whether, in the added constraints, the optimal congestion is computed for the generated traffic matrix. In theory, this value is always 1.0.
  * `model_robust_reformulation_traffic_matrices` enables computing traffic matrices for the robust reformulations. Using this options increases the number of constraints in the problem to solve in order to get the right dual values.

These parameters are only used for problems without uncertainty.

  * `traffic_matrix` is the only traffic matrix that is considered.

These parameters only control the output of the solving process:

  * `locs_f` function that computes the position of the nodes when plotting the graph in 2D. It takes a graph as input and outputs two vectors, first the x positions, then the y positions.
  * `logmessage` is a function that will be called whenever the package produces any textual output. By default, text is redirected to the shell (`println`). This function should take a single string argument, the message to print.
  * `verbose` indicates whether this function (not the complete package) should be explicit about what it is doing (for instance, if it removes demands). This option does not include regular progress logging for long operations.
  * `plot_final_results`: whether plots should be produced when the solving process is done.
  * `plot_each_iteration`: for iterative algorithms, whether plots should be produced at each iteration.
  * `export_lps`: export the LP files (if possible) for each and every (sub)problem that is solved. If the master problem is iteratively built, each iteration will be exported. As the LP format can only represent MILP problems, not all combinations of problem types and solving algorithms can benefit from this parameter.
  * `export_lps_on_error`: export the LP files (if possible) of the (sub)problem being solved when an error occurs. As the LP format can only represent MILP problems, not all combinations of problem types and solving algorithms can benefit from this parameter.
  * `output_folder`: the folder where all file output is supposed to be taking place. This folder must exist beforehand or be an empty string to disable all output.
