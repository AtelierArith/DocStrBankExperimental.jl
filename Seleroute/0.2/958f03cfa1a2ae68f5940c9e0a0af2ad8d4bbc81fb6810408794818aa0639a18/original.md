Data structure holding results of the computations for a routing. All information from intermediate iterations are kept within this object.

  * `data`: a pointer to the `RoutingData` object that was used for the computations.
  * `result`: an `MOI.TerminationStatusCode` indicating the result of the optimiser. This is usually `MOI.OPTIMAL`, but other codes indicate why the solver stopped (`MOI.SLOW_PROGRESS`, `MOI.INFEASIBLE`, etc.). This code is not supposed to be the result of the last iteration, but a summary of the termination of the process: for instance, if the last iteration gives an `MOI.INFEASIBLE` code at the last iteration due to numerical errors, the whole process may show `MOI.SLOW_PROGRESS`.
  * `n_iter`: the number of iterations (the exact meaning of this field depends on the algorithm). Iterations are supposed to be spent in this package, improving/finding a network routing; this should not be a copy of a field from the underlying solver (e.g., simplex iterations). (This field is computed and not explicitly stored in the object.)
  * `n_matrices`: the number of traffic matrices added into the formulation. It may be equal to the number of iterations, depending on the algorithm. (This field is computed and not explicitly stored in the object.)
  * `n_matrices_per_edge`: the number of traffic matrices that were generated, arranged by edge that yielded the traffic matrix, if this definition matches the behaviour of the algorithm.
  * `n_matrices_used`: the number of matrices that are actually used for the solution at any given iteration (i.e. they correspond to tight constraints).
  * `n_cuts`: the number of added constraints.
  * `n_columns`: the number of added columns, for column-generation based algorithms. Its value should be 0 for other algorithms.
  * `n_columns_master`: the number of added columns to the master problem, for column-generation based algorithms. Its value should be 0 for other algorithms. Columns for the subproblems are not counted, if any.
  * `n_columns_subproblems`: the number of added columns to the subproblems, for column-generation based iterative algorithms. Its value should be 0 for other algorithms. Columns for the master problem are not counted, if any.
  * `n_columns_used`: the number of columns actually used for the last solution (i.e. nonzero flow in these paths). Zero for flow-based formulations.

Many different timings are measured for the whole execution (always in milliseconds), with a granularity at most for master-problem iterations (totals are also provided):

  * `time_precompute_ms`: time to prepare the data structures before the actual computations. For instance, it may account for detection of loops or unroutable demands; for column-generation algorithms, it includes the time to generate the first few paths (i.e. before any pricing process can take place). This parameter takes precedence on the one from the given `RoutingData` object (i.e. it may include more operations).
  * `time_create_master_model_ms`: time to create the mathematical formulation of the master problem (or the only problem, if the algorithm is not iterative). In particular, this does not include instanciation of subproblems.
  * `time_create_subproblems_model_ms`: time to create the mathematical formulation of the subproblem(s) (if the algorithm uses at least one). If the algorithm does not use subproblem(s), the value is zero. If the algorithm uses several different subproblems, this variable reports the total time for all subproblems. If the subproblems are solved using dedicated algorithms (such as shortest paths), this time will be zero, but not the solve times.
  * `time_solve_ms`: time to compute the routing, one value per iteration. This time may include more operations than solving the master and subproblems, such as bookkeeping or modifying the master formulation  following the subproblems (new columns/rows).
  * `time_solve_master_model_ms`: time to compute the routing spent in the master problem, one value per iteration. Only time spent in the solver is counted here.
  * `time_solve_subproblems_model_ms`: time to compute the routing spent in the subproblems if any, one value per iteration of the master problem. If several subproblems are solved for one iteration of the master problem, the total time for these subproblems is reported (i.e. only one value in this dictionary per iteration of the master problem). Only time spent in the solver is counted here.
  * `total_time_solve_ms`: total time spent in solving. (This field is computed and not explicitly stored in the object.)
  * `total_time_solve_master_model_ms`: total time spent in solving the master model. (This field is computed and not explicitly stored in the object.)
  * `total_time_solve_subproblems_model_ms`: total time spent in solving the subproblems. (This field is computed and not explicitly stored in the object.)
  * `time_intermediate_export_ms`: time to export the intermediate results, when requested, one value per iteration where there is export.
  * `time_final_export_ms`: time to export the final solution, when requested.
  * `total_time_export_ms`: total time spent in exporting. (This field is computed and not explicitly stored in the object.)
  * `total_time_ms`: total time spent in the whole process (precomputing, solving, exporting). (This field is computed and not explicitly stored in the object.)

The following vectors contain information about the execution of the algorithm. Not all vectors have as many entries as iterations, even though it is expected to be the most likely case.

  * `objectives`: the value of the objective function that is being optimised, at most one per iteration.
  * `matrices`: the demand matrices generated during the execution, when their output is requested. It may contain a single matrix if the algorithm does not generate new matrices during its execution. There may be no such matrix at the last iteration. There may be several matrices for some iterations.
  * `routings`: the various routings generated during the execution. There must be at most one routing per iteration, except when requested.
  * `master_model`: the final optimisation model, with all generated cuts and columns (if relevant for the algorithm being used). Solving it should give the same solution as `routings[end]`.
