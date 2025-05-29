```
used(buf)
```

Return the number of elements used in buffer `buf`.

If the buffer is used with [`reshape_buf!`](@ref), `-1` is returned.

For `ThreadsBuffer`, return the number of elements used in the buffer of the current thread.
