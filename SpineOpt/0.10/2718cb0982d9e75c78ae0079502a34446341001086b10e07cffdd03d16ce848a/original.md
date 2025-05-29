```
write_report_from_intermediate_results(intermediate_results_folder, default_url; <keyword arguments>)
```

Collect results generated on a previous, unsuccessful SpineOpt run from `intermediate_results_folder`, and write the corresponding report(s) to `url_out`. A new Spine database is created at `url_out` if one doesn't exist.

# Arguments

  * `alternative::String=""`: if non empty, write results to the given alternative in the output DB.
  * `log_level::Int=3`: an integer to control the log level.
