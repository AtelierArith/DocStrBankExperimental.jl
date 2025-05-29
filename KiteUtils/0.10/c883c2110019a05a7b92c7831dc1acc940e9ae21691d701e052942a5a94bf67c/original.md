```
log!(logger::Logger, state::SysState)
```

Log a state in a logger object. Do nothing if the preallocated size would be exceeded. Returns the current number of elements of the log.
