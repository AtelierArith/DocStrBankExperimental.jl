```
SRLogger(logger::AbstractLogger; log_interval::Int=100)
```

A logger for symbolic regression that wraps another logger.

# Arguments

  * `logger`: The base logger to wrap
  * `log_interval`: Number of steps between logging events. Default is 100 (log every 100 steps).
