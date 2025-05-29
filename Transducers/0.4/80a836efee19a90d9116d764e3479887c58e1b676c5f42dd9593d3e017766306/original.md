```
DistributedEx(; pool, basesize, threads_basesize, simd)
```

Distributed fold executor.  It can be passed to APIs from packages such as Folds.jl and FLoops.jl to run the algorithm sequentially.

See also: [`foldxd`](@ref), [`SequentialEx`](@ref) and [`ThreadedEx`](@ref).

# Keyword Arguments

  * `pool::AbstractWorkerPool`: Passed to `Distributed.remotecall`.
  * `basesize::Integer = amount(array) ÷ nworkers()`: A size of chunk in `array` that is processed by each worker.  A smaller size may be required when computation time for processing each item can fluctuate a lot.
  * `threads_basesize::Integer = basesize ÷ nthreads()`: A size of chunk in `array` that is processed by each task in each worker process. The default setting assumes that the number of threads used in all workers are the same.  For heterogeneous setup where each worker process has different number of threads, it may be required to use smaller `threads_basesize` *and* `basesize` to get a good performance.
  * `simd`: If `true` or `:ivdep`, enable SIMD using `Base.@simd`.  If `:ivdep`, use `@simd ivdep for ... end` variant.  Read Julia manual of `Base.@simd` to understand when it is appropriate to use this option.  For example, `simd = :ivdep` *must not* be used with stateful transducer like [`Scan`](@ref).  If `false` (default), `Base.@simd` is not used.

# Examples

```jldoctest
julia> using Folds

julia> Folds.sum(1:3, DistributedEx())
6
```
