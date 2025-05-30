```
GreedyScheduler (aka :greedy)
```

A greedy dynamic scheduler. The elements are put into a shared workqueue and dynamic, non-sticky, tasks are spawned to process the elements of the queue with each task taking a new element from the queue as soon as the previous one is done.

Note that elements are processed in a non-deterministic order, and thus a potential reducing function **must** be [commutative](https://en.wikipedia.org/wiki/Commutative_property) in addition to being associative, or you could get incorrect results!

Can be good choice for load-balancing slower, uneven computations, but does carry some additional overhead.

## Keyword arguments:

  * `ntasks::Int` (default `nthreads()`):

      * Determines the number of parallel tasks to be spawned.
      * Setting `ntasks < nthreads()` is an effective way to use only a subset of the available threads.
  * `chunking::Bool` (default `false`):

      * Controls whether input elements are grouped into chunks (`true`) or not (`false`) before put into the shared workqueue. This can improve the performance especially if there are many iterations each of which are computationally cheap.
      * If `nchunks` or `chunksize` are explicitly specified, `chunking` will be automatically set to `true`.
  * `nchunks::Integer` (default `10 * nthreads()`):

      * Determines the number of chunks (that will eventually be put into the shared workqueue).
      * Increasing `nchunks` can help with [load balancing](https://en.wikipedia.org/wiki/Load_balancing_(computing)). For `nchunks <= nthreads()` there are not enough chunks for any load balancing.
  * `chunksize::Integer` (default not set)

      * Specifies the desired chunk size (instead of the number of chunks).
      * The options `chunksize` and `nchunks` are **mutually exclusive** (only one may be a positive integer).
  * `minchunksize::Union{Integer, Nothing}` (default `nothing`)

      * Sets a lower bound on the size of chunks. This argument takes priority over `nchunks`, so `treduce(+, 1:10; nchunks=10, minchunksize=5)` will only operate on `2` chunks for example.
  * `split::Union{Symbol, OhMyThreads.Split}` (default `OhMyThreads.RoundRobin()`):

      * Determines how the collection is divided into chunks (if chunking=true).
      * See [ChunkSplitters.jl](https://github.com/JuliaFolds2/ChunkSplitters.jl) for more details and available options. We also allow users to pass `:consecutive` in place of `Consecutive()`, and `:roundrobin` in place of `RoundRobin()`
