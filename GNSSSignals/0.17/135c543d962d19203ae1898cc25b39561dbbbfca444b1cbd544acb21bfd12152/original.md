```julia
get_code(system, phase, prn)

```

Get code of type <: `AbstractGNSS` at phase `phase` of PRN `prn`.

```julia-repl
julia> get_code(GPSL1(), 1200.3, 1)
```
