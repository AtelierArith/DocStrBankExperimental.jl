```
getnumanode(; threadid = nothing)
```

Returns the ID (starting at zero) of the NUMA node corresponding to the CPU thread on which the calling thread is currently running. A `threadid` may be provided to consider a Julia thread that is different from the calling one.
