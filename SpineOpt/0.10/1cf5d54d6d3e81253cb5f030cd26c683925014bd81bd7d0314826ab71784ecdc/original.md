```
generate_forced_outages(url_in, url_out; <keyword arguments>)
```

Generate forced outages from the contents of `url_in` and write them to `url_out`. At least `url_in` must point to a valid Spine database. A new Spine database is created at `url_out` if one doesn't exist.

To generate forced outages for a unit, specify `mean_time_to_failure` and optionally `mean_time_to_repair` for that unit as a duration in the input DB.

Parameter `units_unavailable` will be written for those units in the output DB holding a time series.

# Arguments

  * `alternative::String=""`: if non empty, write results to the given alternative in the output DB.
  * `filters::Dict{String,String}=Dict("tool" => "object_activity_control")`: a dictionary to specify filters. Possible keys are "tool" and "scenario". Values should be a tool or scenario name in the input DB.

# Example

```
using SpineOpt
m = generate_forced_outages(
    raw"sqlite:///C:\path\to\your\input_db.sqlite", 
    raw"sqlite:///C:\path\to\your\output_db.sqlite"
)
```
