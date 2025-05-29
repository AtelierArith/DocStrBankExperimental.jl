```
threadinfo(;
    groupby = :sockets,
    threadpool = :default,
    blas = false,
    slurm = false,
    hints = false,
    compact = true,
    hyperthreads = SysInfo.hyperthreading_is_enabled(),
    efficiency = SysInfo.ncorekinds() > 1,
    masks = false,
    coregaps = SysInfo.hyperthreading_is_enabled(),
    logical = false,
    color = true,
    blocksize = choose_blocksize()
)
```

Print information about Julia threads, e.g. on which CPU-threads (i.e. cores if hyperthreading is disabled) they are running.

# Keyword arguments

  * `groupby`: Options are `:sockets`, `:numa`, `:cores`, or `:none`.
  * `threadpool`: Only consider Julia threads in the given thread pool.                                 Supported values are `:default`, `:interactive`, and                                 `:all`.
  * `blas`: Visualize BLAS threads instead of Julia threads.
  * `slurm`: Only show the part of the system that is covered by the active SLURM allocation.
  * `hints`: Try to give some hints about how to improve the threading related settings.
  * `compact`: Toggle between compact and "cores before hyperthreads" ordering.
  * `hyperthreads`: If `true`, we (try to) highlight CPU-threads that aren't the first threads within a CPU-core.
  * `efficiency`: If `true`, we highlight (underline) CPU-threads that belong to efficiency cores.
  * `masks`: Show the affinity masks of all Julia threads.
  * `coregaps`: Put an extra space ("gap") between different CPU-cores, when printing.
  * `logical`: Toggle between logical and "physical" CPU-thread indices.
  * `color`: Toggle between colored and black-and-white output.
  * `blocksize`: Wrap to a new line after `blocksize` many CPU-threads.  May also be set to `:numa` in which case the line break will occur after each numa domain.
