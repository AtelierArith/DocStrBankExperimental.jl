```
pflat(p::NWParameter)
pflat(s::NWState)
```

Retrieve the wrapped flat array representation of the parameters. The order of parameters in this flat representation corresponds exactly to the order given by [`parameter_symbols`](@ref).
