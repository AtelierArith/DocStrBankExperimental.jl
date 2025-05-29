```
ThreadPools.readlog(io) -> Dict of (thread # => job list)
```

Analyzes the output of a [`LoggedThreadPool`](@ref) and produces the history of each job on each thread.  

Each job in the job list is a struct of:

```
struct Job
    id    :: Int
    tid   :: Int
    start :: Float64
    stop  :: Float64
end
```

The default sorting order of the jobs in each thread are by stop time.  `io` can either be an IO object or a filename. 

# Example

```julia
julia> log = ThreadPools.readlog("mylog.txt")
Dict{Int64,Array{ThreadPools.Job,1}} with 3 entries:
  4 => ThreadPools.Job[Job(3, 4, 0.016, 0.327), Job(6, 4, 0.327, 0.928)]
  2 => ThreadPools.Job[Job(2, 2, 0.016, 0.233), Job(5, 2, 0.233, 0.749)]
  3 => ThreadPools.Job[Job(1, 3, 0.016, 0.139), Job(4, 3, 0.139, 0.546)]
```
