```
default_units(::Union{Type{AbstractSpec},Type{property_function}})
```

returns a default unit of a spec

# Examples

```julia-repl
default_units(pressure) #function name
Pa

default_units(Gibbs{MOLAR}) #spec type
J/mol
```
