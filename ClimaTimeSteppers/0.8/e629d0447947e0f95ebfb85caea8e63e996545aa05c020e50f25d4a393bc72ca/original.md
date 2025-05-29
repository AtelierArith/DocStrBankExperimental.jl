```
UpdateEveryDt(dt)
```

An `UpdateSignalHandler` that performs the update whenever it is `needs_update!` with an `UpdateSignal` of type `NewTimeStep` and the difference between the current time and the previous update time is no less than `dt`.
