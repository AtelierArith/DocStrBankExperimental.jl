```
getcpuid(; threadid = nothing)
```

Returns the ID of the CPU thread on which a Julia thread is currently running.

If `threadid=nothing` (default), we query the id directly from the calling thread.
