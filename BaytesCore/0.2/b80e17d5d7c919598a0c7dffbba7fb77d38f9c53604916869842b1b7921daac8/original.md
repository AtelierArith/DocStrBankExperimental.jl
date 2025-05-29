```julia
struct ProgressReport{P<:BaytesCore.ProgressLog, K}
```

Default arguments for logging sampling output during sampling process.

# Fields

  * `bar::Bool`: Boolean if progressbar enabled during sampling run
  * `log::BaytesCore.ProgressLog`: Boolean if output diagnostics should be printed.
  * `kwargs::Any`: Additional ProgressMeter keywords to be used to return output
