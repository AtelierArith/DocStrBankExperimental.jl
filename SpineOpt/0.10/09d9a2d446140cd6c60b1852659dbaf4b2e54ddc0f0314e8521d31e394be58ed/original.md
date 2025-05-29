```
run_spineopt(url_in, url_out; <keyword arguments>)
```

Run SpineOpt using the contents of `url_in` and write report(s) to `url_out`. The argument `url_in` must be either a `String` pointing to a valid Spine database, or a `Dict` (e.g. manually created or parsed from a json file). A new Spine database is created at `url_out` if one doesn't exist.

# Arguments

  * `log_level::Int=3`: an integer to control the log level.
  * `upgrade::Bool=false`: whether or not to automatically upgrade the data structure in `url_in` to latest.
  * `filters::Dict{String,String}=Dict("tool" => "object_activity_control")`: a dictionary to specify filters.  Possible keys are "tool" and "scenario". Values should be a tool or scenario name in the input DB.
  * `templates`: a collection of templates to load on top of the SpineOpt template.  Each template must be a `Dict` with the same structure as the one returned by `SpineOpt.template()`.
  * `mip_solver=nothing`: a MIP solver to use if no MIP solver specified in the DB.
  * `lp_solver=nothing`: a LP solver to use if no LP solver specified in the DB.
  * `use_direct_model::Bool=false`: whether or not to use `JuMP.direct_model` to build the `Model` object.
  * `use_model_names::Bool=true`: whether or not to use the names in the model.
  * `add_bridges::Bool=false` whether or not bridges from JuMP to the solver should be added to the model.
  * `optimize::Bool=true`: whether or not to optimise the model (useful for running tests).
  * `update_names::Bool=false`: whether or not to update variable and constraint names after the model rolls  (expensive).
  * `alternative::String=""`: if non empty, write results to the given alternative in the output DB.
  * `write_as_roll::Int=0`: if greater than 0 and the run has a rolling horizon, then write results every that many  windows.
  * `log_file_path::String=nothing`: if not nothing, log all console output to a file at the given path. The file  is overwritten at each call.
  * `resume_file_path::String=nothing`: only relevant in rolling horizon optimisations with `write_as_roll` greater or  equal than one. If the file at given path contains resume data from a previous run, start the run from that point.  Also, save resume data to that same file as the model rolls and results are written to the output database.

# Example

```julia
using SpineOpt
m = run_spineopt(
    raw"sqlite:///C:\path\to\your\input_db.sqlite", 
    raw"sqlite:///C:\path\to\your\output_db.sqlite";
    filters=Dict("tool" => "object_activity_control", "scenario" => "scenario_to_run"),
    alternative="alternative_to_write_results"
)
```
