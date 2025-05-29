```
FastDownward(
    search::String = "astar",
    heuristic::String = "add",
    h_params::Dict{String, String} = Dict(),
    max_time::Float64 = 300,
    verbose::Bool = false,
    log_stats::Bool = true,
    fd_path::String = get(ENV, "FD_PATH", ""),
    py_cmd::String = get(ENV, "PYTHON", "python")
)
```

Wrapper for the FastDownward planning system [1]. The planner has to be installed locally for this wrapper to be used. Consult the FastDownward documentation for further explanation of options.

[1] M. Helmert, "The Fast Downward Planning System," Journal of Artificial Intelligence Research, vol. 26, pp. 191–246, Jul. 2006, [https://doi.org/10.1613/jair.1705](https://doi.org/10.1613/jair.1705).

# Arguments

  * `search`: String specifying search algorithm (e.g. "astar", "ehc").
  * `heuristic`: String specifying search heuristic (e.g. "add", "lmcut",).
  * `h_params`: Heuristic parameters as a dictionary mapping names to values.
  * `max_time`: Maximum time in seconds before planner times out.
  * `verbose`: Flag to print planner outputs.
  * `log_stats`: Flag to log solution statistics.
  * `fd_path`: Path to `fast_downward.py`.
  * `py_cmd`: Path to Python executable.
