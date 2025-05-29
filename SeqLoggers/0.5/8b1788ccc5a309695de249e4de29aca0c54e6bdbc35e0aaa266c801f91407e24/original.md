```
run_with_logger(f::Function, logger::AbstractLogger, args...)
```

Helper function that applies advanced event logging to the execution of `f(args...)`.

In addition to normal log events (`@info`, ...), the logger catches exceptions to create error log events. Afterwards, the exception will continue propagation as if it had not been caught.

### Inputs

  * `f` – function to execute
  * `args` – function arguments

### Retunrs

Result from applying `f(args...)` including thrown exceptions.

### Notes

The function `run_with_logger` applies a new logger to the function call `f(args...)`. All loggers applied on a "higher level" are replaced for the lifespan of the function call.

### Example

```julia
logger = ConsoleLogger(stderr, Logging.Info)
run_with_logger(logger, -3) do number
    @info "Compute square root for negative number: $number"
    sqrt(number)
end
```
