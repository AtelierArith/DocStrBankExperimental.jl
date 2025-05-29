```
start_logging!(config)
```

Starts logging according to `config[:logging]`.  Possible options for `config[:logging]`:

  * `true` (default): logs `@info`, `@warning`, and `@error` messages to `config[:out_path]/E4ST.log`
  * `"debug"` - logs `@debug`, `@info`, `@warning`, and `@error` messages to `config[:out_path]/E4ST.log`
  * `false` - no logging

To log things, you can use `@info`, `@warn`, or `@debug` as defined in Logging.jl.  Or you can use a convenience method for logging a header, [`log_header`](@ref)

To stop the logger and close its io stream, see [`stop_logging!(config)`](@ref)
