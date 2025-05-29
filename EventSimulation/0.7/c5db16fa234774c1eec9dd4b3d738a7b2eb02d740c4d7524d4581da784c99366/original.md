```
terminate!(s)
```

Empties `s.event_queue` which will lead to termination of simulation unless it is refilled before execution returns to `go!`. Useful for event-triggered termination of simulation.
