```
StaticScheduler (aka :static)
```

A static low-overhead scheduler. Divides the given collection into chunks and then spawns a task per chunk to perform the requested operation in parallel. The tasks are statically assigned to threads up front and are made *sticky*, that is, they are guaranteed to stay on the assigned threads (**no task migration**).

Can sometimes be more performant than `DynamicScheduler` when the workload is (close to) uniform and, because of the lower overhead, for small workloads. Isn't well composable with other multithreaded code though.

## Keyword arguments:

  * `nchunks::Integer` or `ntasks::Integer` (default `nthreads()`):

      * Determines the number of chunks (and thus also the number of parallel tasks).
      * Setting `nchunks < nthreads()` is an effective way to use only a subset of the available threads.
      * For `nchunks > nthreads()` the chunks will be distributed to the available threads in a round-robin fashion.
  * `chunksize::Integer` (default not set)

      * Specifies the desired chunk size (instead of the number of chunks).
      * The options `chunksize` and `nchunks`/`ntasks` are **mutually exclusive** (only one may be non-zero).
  * `minchunksize::Union{Integer, Nothing}` (default `nothing`)

      * Sets a lower bound on the size of chunks. This argument takes priority over `nchunks`, so `treduce(+, 1:10; nchunks=10, minchunksize=5)` will only operate on `2` chunks for example.
  * `chunking::Bool` (default `true`):

      * Controls whether input elements are grouped into chunks (`true`) or not (`false`).
      * For `chunking=false`, the arguments `nchunks`/`ntasks`, `chunksize`, and `split` are ignored and input elements are regarded as "chunks" as is. Hence, there will be one parallel task spawned per input element. Note that, depending on the input, this **might spawn many(!) tasks** and can be costly!
  * `split::Union{Symbol, OhMyThreads.Split}` (default `OhMyThreads.Consecutive()`):

      * Determines how the collection is divided into chunks. By default, each chunk consists of contiguous elements and order is maintained.
      * See [ChunkSplitters.jl](https://github.com/JuliaFolds2/ChunkSplitters.jl) for more details and available options. We also allow users to pass `:consecutive` in place of `Consecutive()`, and `:roundrobin` in place of `RoundRobin()`
      * Beware that for `split=OhMyThreads.RoundRobin()` the order of elements isn't maintained and a reducer function must not only be associative but also **commutative**!
