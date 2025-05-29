```
enter(sched, delay, priority, action, args...; kwargs...)
```

Enter a new event in the queue at a relative time. A variant of enterabs that specifies the time as a relative time. This is actually the more commonly used interface.
