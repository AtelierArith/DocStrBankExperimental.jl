```julia
LogEventTracker() -> InfrastructureSystems.LogEventTracker
LogEventTracker(
    levels
) -> InfrastructureSystems.LogEventTracker

```

Tracks counts of all log events by level.

# Examples

```Julia
LogEventTracker()
LogEventTracker((Logging.Info, Logging.Warn, Logging.Error))
```
