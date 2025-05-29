```
@spec_str(term)
```

Allows an easy instantiation of specification properties, returning a specification type corresponding to the input symbol:

```
spec"t" = Temperature()
```

This property, among with the `spec` function, allows the creation of specification properties at compile time:

```julia-repl
julia> Using Unitful,ThermoState,BenchmarkTools

julia> @btime spec(spec"t",232u"°C",false)
  0.001 ns (0 allocations: 0 bytes)
spec(t = 232[°C])
```
