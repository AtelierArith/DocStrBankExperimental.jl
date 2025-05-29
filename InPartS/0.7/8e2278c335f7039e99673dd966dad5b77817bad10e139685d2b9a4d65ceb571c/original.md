```
BackupCallback{backend}(trigger::AbstractCallback, filename; [warn = IOWARN[]])
```

Creates a callback that dumps the entire simulation state to `filename`.

# Extended help

The entire simulation state, consisting of static parameters and a full snapshot, is saved every time the `trigger` callback is triggered. The data file is truncated before writing.
