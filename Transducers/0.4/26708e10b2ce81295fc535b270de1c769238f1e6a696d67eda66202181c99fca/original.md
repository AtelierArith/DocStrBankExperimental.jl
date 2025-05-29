```
SequentialEx(; simd)
```

Sequential fold executor.  It can be passed to APIs from packages such as Folds.jl and FLoops.jl to run the algorithm sequentially.

See also: [`foldxl`](@ref), [`ThreadedEx`](@ref) and [`DistributedEx`](@ref).

# Keyword Arguments

  * `simd`: If `true` or `:ivdep`, enable SIMD using `Base.@simd`.  If `:ivdep`, use `@simd ivdep for ... end` variant.  Read Julia manual of `Base.@simd` to understand when it is appropriate to use this option.  For example, `simd = :ivdep` *must not* be used with stateful transducer like [`Scan`](@ref).  If `false` (default), `Base.@simd` is not used.

# Examples

```jldoctest
julia> using Folds

julia> Folds.sum(1:3, SequentialEx())
6
```
