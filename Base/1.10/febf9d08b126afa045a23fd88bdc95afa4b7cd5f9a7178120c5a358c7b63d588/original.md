```
@timed
```

A macro to execute an expression, and return the value of the expression, elapsed time, total bytes allocated, garbage collection time, and an object with various memory allocation counters.

In some cases the system will look inside the `@timed` expression and compile some of the called code before execution of the top-level expression begins. When that happens, some compilation time will not be counted. To include this time you can run `@timed @eval ...`.

See also [`@time`](@ref), [`@timev`](@ref), [`@elapsed`](@ref), [`@allocated`](@ref), and [`@allocations`](@ref).

```julia-repl
julia> stats = @timed rand(10^6);

julia> stats.time
0.006634834

julia> stats.bytes
8000256

julia> stats.gctime
0.0055765

julia> propertynames(stats.gcstats)
(:allocd, :malloc, :realloc, :poolalloc, :bigalloc, :freecall, :total_time, :pause, :full_sweep)

julia> stats.gcstats.total_time
5576500
```

!!! compat "Julia 1.5"
    The return type of this macro was changed from `Tuple` to `NamedTuple` in Julia 1.5.

