```julia
MultiLogger(
    loggers::Array{T<:Base.CoreLogging.AbstractLogger}
) -> InfrastructureSystems.MultiLogger

```

Creates a MultiLogger with no event tracking.

# Example

```Julia
MultiLogger([TerminalLogger(stderr), SimpleLogger(stream)])
```
