```julia
configure_logging(
;
    console_level,
    file_level,
    filename
) -> InfrastructureSystems.MultiLogger

```

Creates console and file loggers.

**Note:** Log messages may not be written to the file until flush() or close() is called on the returned logger.

# Arguments

  * `console_level = Logging.Error`: level for console messages
  * `file_level = Logging.Info`: level for file messages
  * `filename::Union{Nothing, AbstractString} = "power-systems.log"`: log file; pass nothing to disable file logging

# Example

```julia
logger = configure_logging(console_level = Logging.Info)
@info "log message"
close(logger)
```
