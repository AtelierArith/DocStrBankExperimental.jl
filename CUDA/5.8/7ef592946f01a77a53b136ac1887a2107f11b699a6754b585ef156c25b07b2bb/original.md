```
default_stream()
```

Return the default stream.

!!! note
    It is generally better to use `stream()` to get a stream object that's local to the current task. That way, operations scheduled in other tasks can overlap.

