```
UpdateEveryN(n, update_signal_type, reset_signal_type = Nothing)
```

An `UpdateSignalHandler` that performs the update every `n`-th time it is `needs_update!` with an `UpdateSignal` of type `update_signal_type`. If `reset_signal_type` is specified, then the counter (which gets incremented from 0 to `n` and then gets reset to 0 when it is time to perform another update) is reset to 0 whenever the signal handler is `needs_update!` with an `UpdateSignal` of type `reset_signal_type`.
