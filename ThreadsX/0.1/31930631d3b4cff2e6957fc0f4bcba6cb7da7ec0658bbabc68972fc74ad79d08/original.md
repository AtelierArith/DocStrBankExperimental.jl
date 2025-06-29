# Threads⨉: Parallelized `Base` functions

[![Stable](https://img.shields.io/badge/docs-stable-blue.svg)](https://juliafolds2.github.io/ThreadsX.jl/stable) [![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://juliafolds2.github.io/ThreadsX.jl/dev)

## tl;dr

Add prefix `ThreadsX.` to functions from `Base` to get some speedup, if supported.  Example:

```jldoctest ThreadsX
julia> using ThreadsX

julia> ThreadsX.sum(gcd(42, i) == 1 for i in 1:10_000)
2857
```

To find out functions supported by ThreadsX.jl, just type `ThreadsX.` + *TAB* in the REPL:

```julia
julia> ThreadsX.
MergeSort       any             findfirst       map!            reduce
QuickSort       collect         findlast        mapreduce       sort
Set             count           foreach         maximum         sort!
StableQuickSort extrema         issorted        minimum         sum
all             findall         map             prod            unique
```

## Interoperability

### Rich collection support

The `reduce`-based functions support any collections that implement [`SplittablesBase.jl`](https://github.com/JuliaFolds2/SplittablesBase.jl) interface including arrays, `Dict`, `Set`, and iterator transformations.  In particular, these functions support iterator comprehension:

```jldoctest ThreadsX
julia> ThreadsX.sum(y for x in 1:10 if isodd(x) for y in 1:x^2)
4917
```

For advanced usage, they also support [`Transducers.eduction`](https://juliafolds2.github.io/Transducers.jl/dev/reference/manual/#Transducers.eduction) constructed with parallelizable transducers.

### OnlineStats.jl

`ThreadsX.reduce` supports an `OnlineStat` from [OnlineStats.jl](https://github.com/joshday/OnlineStats.jl) as the first argument as long as it implements the [merging interface](https://github.com/joshday/OnlineStatsBase.jl#interface):

```jldoctest ThreadsX
julia> using OnlineStats: Mean

julia> ThreadsX.reduce(Mean(), 1:10)
Mean: n=10 | value=5.5
```

## API

ThreadsX.jl is aiming at providing API compatible with `Base` functions to easily parallelize Julia programs.

All functions that exist directly under `ThreadsX` namespace are public API and they implement a subset of API provided by `Base`. Everything inside `ThreadsX.Implementations` is implementation detail. The public API functions of `ThreadsX` expect that the data structure and function(s) passed as argument are "thread-friendly" in the sense that operating on *distinct* elements in the given container from multiple tasks in parallel is safe. For example, `ThreadsX.sum(f, array)` assumes that executing `f(::eltype(array))` and accessing elements as in `array[i]` from multiple threads is safe.  In particular, this is the case if `array` is a `Vector` of immutable objects and `f` is a pure function in the sense it does not mutate any global objects.  Note that it is not required and *not recommended* to use "thread-safe" array that protects accessing `array[i]` by a lock.

In addition to the `Base` API, all functions accept keyword argument `basesize::Integer` to configure the number of elements processed by each thread.  A large value is useful for minimizing the overhead of using multiple threads.  A small value is useful for load balancing when the time to process single item varies a lot from item to item. The default value of `basesize` for each function is currently an implementation detail.

ThreadsX.jl API is deterministic in the sense that the same input produces the same output, independent of how `julia`'s task scheduler decide to execute the tasks.  However, note that `basesize` is a part of the input which may be set based on `Threads.nthreads()`.  To make the result of the computation independent of `Threads.nthreads()` value, `basesize` must be specified explicitly.

## Limitations

  * Keyword argument `dims` is not supported yet.
  * (There are probably more.)

## Implementations

Most of `reduce`-based functions are implemented as thin wrappers of [`Transducers.jl`](https://github.com/JuliaFolds2/Transducers.jl).

Custom collections can support ThreadsX.jl API by implementing [`SplittablesBase.jl`](https://github.com/JuliaFolds2/SplittablesBase.jl) interface.
