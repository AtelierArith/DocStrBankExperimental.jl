```
ThreadedEx(; basesize, stoppable, nestlevel, simd)
```

Multi-threaded fold executor.  This is the default [^1] parallel executor used by Folds.jl and FLoops.jl.

See also: [`foldxt`](@ref), [`SequentialEx`](@ref) and [`DistributedEx`](@ref).

[^1]: More specifically, Folds.jl and FLoops.jl uses [`PreferParallel`](@ref)   which in turn defaults to `ThreadedEx`.

# Keyword Arguments

  * `basesize::Integer = amount(reducible) ÷ nthreads()`: A size of chunk in `reducible` that is processed by each worker.  A smaller size may be required when:

      * computation time for processing each item fluctuates a lot
      * computation can be terminated by [`reduced`](@ref) or transducers using it, such as [`ReduceIf`](@ref)
  * `stoppable::Bool`: [This option usually does not have to be set manually.]  The threaded fold executed in the "stoppable" mode used for optimizing reduction with [`reduced`](@ref) has a slight overhead if `reduced` is not used.  This mode can be disabled by passing `stoppable = false`.  It is usually automatically detected and set appropriately.  Note that this option is purely for optimization and does not affect the result value.
  * `nestlevel::Union{Integer,Val}`: Specify how many inner `Cat` (flatten) transducers to be multi-threaded (using [`TCat`](@ref)). It must be a positive integer, `Val` of positive integer, or `Val(:inf)`.  `Val(:inf)` means to use multi-threading for all `Cat` transducers.  Note that `Cat` transducer should be statically known. That is to say, the fold implementation sees two `Cat`s in `... |> Map(f) |> Cat() |> Cat()` but only one `Cat` in `... |> Map(x -> f(x) |> Cat()) |> Cat()` even though they are semantically identical.
  * `simd`: If `true` or `:ivdep`, enable SIMD using `Base.@simd`.  If `:ivdep`, use `@simd ivdep for ... end` variant.  Read Julia manual of `Base.@simd` to understand when it is appropriate to use this option.  For example, `simd = :ivdep` *must not* be used with stateful transducer like [`Scan`](@ref).  If `false` (default), `Base.@simd` is not used.

# Examples

```jldoctest
julia> using Folds

julia> Folds.sum(1:3, ThreadedEx(basesize = 1))
6
```
