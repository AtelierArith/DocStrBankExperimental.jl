```
pinthreads(cpuids;
    nthreads   = nothing,
    force      = true,
    warn       = is_first_pin_attempt(),
    threadpool = :default
)
```

Pin Julia threads to an explicit or implicit list of CPU IDs. The latter can be specified in three ways:

1. by passing one of several predefined symbols (e.g. `pinthreads(:cores)` or `pinthreads(:sockets)`),
2. by providing a logical specification via helper functions (e.g. `pinthreads(numa(2, 1:4))`),
3. explicitly (e.g. `0:3` or `[0,12,4]`).

See `??pinthreads` for more information on these variants and keyword arguments.

# Keyword arguments

If set, the keyword argument `nthreads` serves as a cutoff, that is, the first `min(length(cpuids), nthreads)` Julia threads will get pinned.

The keyword argument `threadpool` can be used to indicate the pool of Julia threads that should be considered. Supported values are `:default` (default), `:interactive`, or `:all`. On Julia >= 1.11, there is also experimental support for `:gc`.

If `force=false`, threads will only get pinned if this is the very first pin attempt (otherwise the call is a no-op). This may be particularly useful for packages that merely want to specify an "default pinning" that can be overwritten by the user.

The option `warn` toggles general warnings, such as unwanted interference with BLAS thread settings.

# Extended help

**1) Predefined Symbols**

  * `:cputhreads` or `:compact`: successively pin to all available CPU-threads.
  * `:cores`: spread threads across all available cores, only use hyperthreads if necessary.
  * `:sockets`: spread threads across sockets (round-robin), only use hyperthreads if             necessary. Set `compact=true` to get compact pinning within each socket.
  * `:numa`: spread threads across NUMA/memory domains (round-robin), only use hyperthreads          if necessary. Set `compact=true` to get compact pinning within each NUMA/memory          domain.
  * `:random`: pin threads randomly to CPU-threads
  * `:current`: pin threads to the CPU-threads they are currently running on
  * `:firstn`: pin threads to CPU-threads in order according to there OS index.
  * `:affinitymask`: pin threads to different CPU-threads in accordance with the process                  affinity. By default, `hyperthreads_last=true`.

**2) Logical Specification**

The functions [`node`](@ref), [`socket`](@ref), [`numa`](@ref), and [`core`](@ref) can be used to to specify CPU IDs of/within a certain domain. Moreover, the functions [`sockets`](@ref) and [`numas`](@ref) can be used to express a round-robin scatter policy between sockets or NUMA domains, respectively.

*Examples (domains):*

  * `pinthreads(socket(1, 1:3))` # pin to the first 3 cores in the first socket
  * `pinthreads(socket(1, 1:3; compact=true))` # pin to the first 3 CPU-threads in the first socket
  * `pinthreads(numa(2, [2,4,6]))` # pin to the second, the fourth, and the sixth cores in the second NUMA/memory domain
  * `pinthreads(node(ncores():-1:1))` # pin threads to cores in reversing order (starting at the end of the node)
  * `pinthreads(sockets())` # scatter threads between sockets, cores before hyperthreads

Different domains can be concatenated by providing them in a vector or as separate arguments to `pinthreads`.

*Examples (concatenation):*

  * `pinthreads([socket(1, 1:3), numa(2, 4:6)])`
  * `pinthreads(socket(1, 1:3), numa(2, 4:6))`

**3) Explicit**

Simply provide an `AbstractVector{<:Integer}` of CPU IDs. The latter are expected to be "physical" OS indices (e.g. from hwloc or lscpu) that start at zero!
