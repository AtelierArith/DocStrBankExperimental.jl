```
rate(r::Rate)
```

Returns the untyped scalar interest rate represented by the `Rate`.

# Examples

```julia-repl
julia> r =Continuous(0.03)
Yields.Rate{Float64, Continuous}(0.03, Continuous())

julia> rate(r)
0.03
```
