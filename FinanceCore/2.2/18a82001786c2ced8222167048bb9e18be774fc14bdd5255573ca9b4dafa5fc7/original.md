```
Periodic(frequency)
```

A type representing periodic interest compounding with the given frequency. 

`frequency` will be converted to an `Integer`, and will round up to 8 decimal places (otherwise will throw an `InexactError`). 

# Examples

Creating a semi-annual bond equivalent yield:

```julia-repl
julia> Rate(0.01,Periodic(2))
Rate(0.01, Periodic(2))
```

See also: [`Continuous`](@ref)
