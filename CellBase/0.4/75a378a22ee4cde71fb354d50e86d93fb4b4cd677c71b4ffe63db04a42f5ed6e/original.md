Type representing a composition

The Composition type supports index access:

```julia-repl
julia> comp = Composition(:CO2)
Composition(:CO2)
julia> comp[:C] 
1
```

Internally, the speices and quantities are stored as two vectors, yet the interface mimics that of a `Dict{Sybmol,Float64}`.
