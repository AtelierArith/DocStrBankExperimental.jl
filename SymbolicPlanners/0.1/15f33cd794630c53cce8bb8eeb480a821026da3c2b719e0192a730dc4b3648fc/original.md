```
Pyperplan(
    search::String = "astar",
    heuristic::String = "add",
    log_level::String = "info",
    log_stats::Bool = true,
    max_time::Float64 = 300,
    verbose::Bool = false,
    py_cmd::String = get(ENV, "PYTHON", "python")
)
```

Wrapper for the Pyperplan lightweight STRIPS planner [1]. The planner has to be installed locally for this wrapper to be used. Consult the Pyperplan documentation for further explanation of options.

[1] Y. Alkhazraji et al., "Pyperplan." Zenodo, 2020. [https://doi.org/10.5281/zenodo.3700819](https://doi.org/10.5281/zenodo.3700819).

# Arguments

  * `search`: String specifying search algorithm (e.g. "astar", "gbf").
  * `heuristic`: String specifying search heuristic (e.g. "hadd", "hmax",).
  * `log_level`: How much information to log when running the planner.
  * `log_stats`: Flag to log solution statistics.
  * `max_time`: Maximum time in seconds before planner times out.
  * `verbose`: Flag to print planner outputs.
  * `py_cmd`: Path to Python executable.
