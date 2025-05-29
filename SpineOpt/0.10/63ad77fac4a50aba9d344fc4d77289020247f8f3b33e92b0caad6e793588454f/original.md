```
write_report(m, url_out; <keyword arguments>)
```

Write report(s) from given SpineOpt model to `url_out`. A new Spine database is created at `url_out` if one doesn't exist.

# Arguments

  * `alternative::String=""`: if non empty, write results to the given alternative in the output DB.
  * `log_level::Int=3`: an integer to control the log level.
