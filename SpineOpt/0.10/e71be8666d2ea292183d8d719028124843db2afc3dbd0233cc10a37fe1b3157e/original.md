```
solve_model!(m; <keyword arguments>)
```

Solve given SpineOpt model and save outputs.

# Arguments

  * `log_level::Int=3`: an integer to control the log level.
  * `update_names::Bool=false`: whether or not to update variable and constraint names after the model rolls  (expensive).
  * `write_as_roll::Int=0`: if greater than 0 and the run has a rolling horizon, then write results every that many  windows.
  * `resume_file_path::String=nothing`: only relevant in rolling horizon optimisations with `write_as_roll` greater or  equal than one. If the file at given path contains resume data from a previous run, start the run from that point.  Also, save resume data to that same file as the model rolls and results are written to the output database.
  * `calculate_duals::Bool=false`: whether or not to calculate duals after the model solve.
  * `output_suffix::NamedTuple=(;)`: to add to the outputs.
  * `log_prefix::String`="": to prepend to log messages.
