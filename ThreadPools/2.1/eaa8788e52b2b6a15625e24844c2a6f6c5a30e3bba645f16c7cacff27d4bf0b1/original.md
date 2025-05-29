```
ThreadPools.showstats([io, ]log)
```

Produces a statistical analysis of the provided log.

# Example

```julia
julia> ThreadPools.showstats("mylog.txt")

    Total duration: 1.542 s
    Number of jobs: 8
    Average job duration: 0.462 s
    Minimum job duration: 0.111 s
    Maximum job duration: 0.82 s

    Thread 2: Duration 1.542 s, Gap time 0.0 s
    Thread 3: Duration 1.23 s, Gap time 0.0 s
    Thread 4: Duration 0.925 s, Gap time 0.0 s

```
