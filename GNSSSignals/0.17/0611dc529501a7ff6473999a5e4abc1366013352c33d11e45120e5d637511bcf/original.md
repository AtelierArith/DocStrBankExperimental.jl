```julia
get_code_unsafe(system, phase, prn)

```

Get code. It is unsafe because it omits the modding. The phase will not be wrapped by the code length. The phase has to be smaller than the code length incl. secondary code.

```julia-repl
julia> get_code(GPSL1(), 1200.3, 1)
```
