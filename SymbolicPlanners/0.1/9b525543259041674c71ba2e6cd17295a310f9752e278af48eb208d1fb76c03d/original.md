```
ENHSP(
    search::String = "astar",
    heuristic::String = "add",
    h_mult::Float64 = 1.0,
    log_stats::Bool = true,
    max_time::Float64 = 300,
    verbose::Bool = false,
    enhsp_path::String = get(ENV, "ENHSP_PATH", ""),
    java_cmd::String = get(ENV, "JAVA", "java")
)
```

Wrapper for the Expressive Numeric Heuristic Search Planner (ENHSP) [1]. The planner has to be installed locally for this wrapper to be used. Consult the ENHSP documentation for further explanation of options.

[1] E. Scala et al., "ENHSP", [https://sites.google.com/view/enhsp/](https://sites.google.com/view/enhsp/).

# Arguments

  * `search`: String specifying search algorithm (e.g. "gbfs", "WAStar").
  * `heuristic`: String specifying search heuristic (e.g. "hadd", "aibr",).
  * `h_mult`: Heuristic multiplier for weighted A*.
  * `log_stats`: Flag to log solution statistics.
  * `max_time`: Maximum time in seconds before planner times out.
  * `verbose`: Flag to print planner outputs.
  * `enhsp_path`: Path to `enhsp.jar`.
  * `java_cmd`: Path to Java executable.
