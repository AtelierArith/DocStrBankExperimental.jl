```
was_clock_reset(inlet::StreamInlet)
```

Query whether the clock was potentially reset since the last call to was*clock*reset().

This is rarely-used function is only needed for applications that combine multiple time_correction values to estimate precise clock drift if they should tolerate cases where the source machine was hot-swapped or restarted.
