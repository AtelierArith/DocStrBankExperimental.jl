```
DynamicScheduler (aka :dynamic)
```

The default dynamic scheduler. Divides the given collection into chunks and then spawns a task per chunk to perform the requested operation in parallel. The tasks are assigned to threads by Julia's dynamic scheduler and are non-sticky, that is, they can migrate between threads.

Generally preferred since it is flexible, can provide load balancing, and is composable with other multithreaded code.

## Keyword arguments:

  * `nchunks::Integer` or `ntasks::Integer` (default `nthreads(threadpool)`):

      * Determines the number of chunks (and thus also the number of parallel tasks).
      * Increasing `nchunks` can help with [load balancing](https://en.wikipedia.org/wiki/Load_balancing_(computing)), but at the expense of creating more overhead. For `nchunks <= nthreads()` there are not enough chunks for any load balancing.
      * Setting `nchunks < nthreads()` is an effective way to use only a subset of the available threads.
  * `chunksize::Integer` (default not set)

      * Specifies the desired chunk size (instead of the number of chunks).
      * The options `chunksize` and `nchunks`/`ntasks` are **mutually exclusive** (only one may be a positive integer).
  * `minchunksize::Union{Integer, Nothing}` (default `nothing`)

      * Sets a lower bound on the size of chunks. This argument takes priority over `nchunks`, so `treduce(+, 1:10; nchunks=10, minchunksize=5)` will only operate on `2` chunks for example.
  * `split::Union{Symbol, OhMyThreads.Split}` (default `OhMyThreads.Consecutive()`):

      * Determines how the collection is divided into chunks (if chunking=true). By default, each chunk consists of contiguous elements and order is maintained.
      * See [ChunkSplitters.jl](https://github.com/JuliaFolds2/ChunkSplitters.jl) for more details and available options. We also allow users to pass `:consecutive` in place of `Consecutive()`, and `:roundrobin` in place of `RoundRobin()`
      * Beware that for `split=OhMyThreads.RoundRobin()` the order of elements isn't maintained and a reducer function must not only be associative but also **commutative**!
  * `chunking::Bool` (default `true`):

      * Controls whether input elements are grouped into chunks (`true`) or not (`false`).
      * For `chunking=false`, the arguments `nchunks`/`ntasks`, `chunksize`, and `split` are ignored and input elements are regarded as "chunks" as is. Hence, there will be one parallel task spawned per input element. Note that, depending on the input, this **might spawn many(!) tasks** and can be costly!
  * `threadpool::Symbol` (default `:default`):

      * Possible options are `:default` and `:interactive`.
      * The high-priority pool `:interactive` should be used very carefully since tasks on this threadpool should not be allowed to run for a long time without `yield`ing as it can interfere with [heartbeat](https://en.wikipedia.org/wiki/Heartbeat_(computing)) processes.
