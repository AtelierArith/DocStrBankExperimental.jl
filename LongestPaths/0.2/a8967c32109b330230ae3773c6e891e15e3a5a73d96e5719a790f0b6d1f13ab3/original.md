```
find_longest_path(graph, first_vertex = 1, last_vertex = 0)
```

Find the longest simple path in `graph` starting from `first_vertex` and ending in `last_vertex`. No vertex may be visited more than once. If `last_vertex` is 0, the path may end anywhere. `first_vertex` cannot be 0.

```
find_longest_cycle(graph, first_vertex = 0)
```

Find the longest simple cycle in `graph` that includes `first_vertex`. No vertex may be visited more than once. If `first_vertex` is 0, the cycle can be anywhere.

Given sufficient time and memory, these will succeed in finding the longest path or cycle, but since finding the longest path/cycle is an NP-hard problem, the required time will grow quickly with the graph size.

For the time being, `graph` must be a **directed** graph from the `Graphs` package. The algorithm works for undirected graphs if they are represented as directed graphs with pairs of edges in both directions.

```
find_longest_path(...; kwargs)
find_longest_cycle(...; kwargs)
```

By adding keyword arguments it is possible to guide the search or obtain non-optimal solutions and upper bounds in shorter time than the full solution.

Note: Unless otherwise specified, both paths and cycles are called "paths" in the following and they are always assumed to be simple, i.e. no repeated vertices are allowed.

*Keyword arguments:*

  * `weights`: Edge weights for weighted longest path searches. If omitted all weights are implicitly one. Specified as a dictionary mapping tuples to numbers. `(v1, v2) => w` means that the edge from `v1` to `v2` has the weight `w`.
  * `initial_path`: Search can be warmstarted by providing a path as a vector of vertices. If the provided vertices do not follow a valid simple path, they are ignored.
  * `lower_bound`: User provided lower bound. Search will stop when the upper bound reaches `lower_bound`, even if no path of that length has been found. The provided `lower_bound` will be ignored if a stronger bound is found during search.
  * `upper_bound`: User provided upper bound. Search will stop when the lower bound reaches `upper_bound`, even if a longer path exists. The provided `upper_bound` will be ignored if a stronger bound is found during search.
  * `solver_mode`: Search can be made in three different modes, `"lp"`, `"ip"`, or `"lp+ip"`. In the default `"ip"` mode, integer programs are solved. This can be slow but is guaranteed to eventually find the optimal solution. In the `"lp"` mode only the linear program relaxations are solved. This is unlikely to find a long path but will quickly find good upper bounds. The final `"lp+ip"` mode alternates between `"lp"` and `"ip"` mode and is sometimes more efficient than `"ip"` only to find the optimal solution.
  * `cycle_constraint_mode`: During the search, cycles that are unconnected to the path will be found and iteratively eliminated by adding constraints to the integer programs or the linear program relaxations. Different kinds of constraints can be added for this purpose and `cycle_constraint_mode` can be set to `"cutset"`, `"cycle"` or `"both"`. It is likely that the default `"cutset"` option is the best choice.
  * `initial_cycle_constraints`: By setting this larger than the default value 0, all cycles in the graph of length up to this number will be eliminated from the search before starting. This gives a tradeoff between the number of iterations needed and the time required for each iteration. It probably does not pay off to set this higher than about 3, and possibly 0 is the best setting.
  * `max_iterations`: Stop search after this number of iterations. Defaults to a very high number.
  * `time_limit`: Stop search after this number of seconds. Defaults to a very high number.
  * `solver_time_limit`: Maximum time to spend in each iteration to solve integer programs. This will be gradually increased if the IP solver does not find a useful solution in the allowed time. LP solutions are not affected by this option and are always solved to optimality. Defaults to 10 seconds.
  * `max_gap`: Allowed gap for IP solutions. This will automatically be reduced to be smaller than the distance between the lower and upper bounds. Default is 0. Higher values can speed up the early iterations in `"ip"` mode.
  * `use_ip_warmstart`: Use warmstart when solving integer programs. Normally this speeds up the solution substantially but it also causes the Cbc solver to emit trace outputs. Default is true.
  * `log_level`: Amount of verbosity during search. 0 is maximally quiet. The default value 1 only prints progress for each iteration. Higher values add diagnostics from the IP solver calls.
  * `new_longest_path_callback`: A function provided here will be called every time a new longest path has been found. This gives an opportunity to save partial solutions of very long running searches. The function should accept one argument, which is the longest path expressed as a vector of vertices. Default is a function that does nothing. The return value from the function is ignored.
  * `iteration_callback`: A function provided here is called during each iteration. The function should take one argument which is a named tuple with diagnostic information, see the code for exact specifications. Return `true` to continue search and `false` to stop search. The default is the `print_iteration_data` function.
  * `preprocess`: Whether to preprocess the graph before starting the search. Defaults to true. This performs the following steps:

    1. Convert undirected graphs to directed graphs.
    2. Remove self-loops.
    3. Remove vertices and edges which can provably not be part of an optimal solution.

    The main reason to disable this are to save time and/or memory if you know that the preprocessing will not be helpful. The `iteration_callback` and the internals of the returned result will relate to the preprocessed graph if `preprocess` is enabled, but vertices can be mapped back to the original graph via the provided `vertex_mapping`.
  * `reduce_unbranched`: Whether to optimize the graph such that vertices with two neighbors are eliminated where possible. Defaults to false. This turns unweighted searches into weighted searches. The same caveats with respect to introspection as `preprocess` apply.

The return value is of the `LongestPathOrCycle` type and contains the following fields:

  * `is_cycle`: Whether the search produced a cycle or a path.
  * `lower_bound`: Lower bound for the length of the longest path.
  * `upper_bound`: Upper bound for the length of the longest path.
  * `longest_path`: Vector of the vertices in the longest found path.
  * `internals`: Dict containing a variety of information about the search.

Notes:

  * Path lengths are reported by number of edges, not number of vertices. For cycles these are the same, for paths the number of edges is one less than the number of vertices. For weighted searches the length is the sum of the weights along the path.
  * If there is no outgoing edge from `first_vertex` in a path search going anywhere, the length is reported as 0 and the returned `longest_path` contains the single vertex `first_vertex`. This is also the case if `first_vertex == last_vertex`.
  * In other searches, if there exists no path or cycle matching the specifications, the length is reported as 0 and the returned `longest_path` is empty.
  * In weighted searches, if the weights are of an `Integer` type, the search knows that the optimum is an integer value and can round bounds more aggressively.
  * Weights may be zero or negative. If all weights are non-positive the problem effectively becomes a shortest path problem, which is fine but can be solved considerably more efficiently with other methods.
