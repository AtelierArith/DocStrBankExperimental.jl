```
@profiler exp [kwargs...]
```

Clear currently collected profile traces, profile the provided expression and show   it via `Juno.profiler()`.

Any keyword argument that [`FlameGraphs.flamegraph`](@ref) can take could be given   as optional arugments `kwargs...`

```julia
# profile a function call
@profiler fname(fargs)

# include ccalls and compress recursive calls
@profiler fname(fargs) C = true recur = :flat
```
