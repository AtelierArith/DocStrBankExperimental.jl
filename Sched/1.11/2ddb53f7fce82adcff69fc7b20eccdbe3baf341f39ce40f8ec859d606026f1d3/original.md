```
enterabs(sched, time_, priority, action, args...; kwargs...)
```

Enter a new event in the queue at an absolute time. Returns an ID for the event which can be used to remove it, if necessary.
