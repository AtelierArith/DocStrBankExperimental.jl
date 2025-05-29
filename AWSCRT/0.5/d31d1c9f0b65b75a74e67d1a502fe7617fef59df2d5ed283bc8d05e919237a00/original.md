```
EventLoopGroup(num_threads::Union{Int,Nothing} = nothing, cpu_group::Union{Int,Nothing} = nothing)
```

A collection of event-loops. An event-loop is a thread for doing async work, such as I/O.

Arguments:

  * `num_threads (Union{Int,Nothing}) (default=nothing)`: Maximum number of event-loops to create. If unspecified, one is created for each processor on the machine.
  * `cpu_group (Union{Int,Nothing}) (default=nothing)`: Optional processor group to which all threads will be pinned. Useful for systems with non-uniform memory access (NUMA) nodes. If specified, the number of threads will be capped at the number of processors in the group.
