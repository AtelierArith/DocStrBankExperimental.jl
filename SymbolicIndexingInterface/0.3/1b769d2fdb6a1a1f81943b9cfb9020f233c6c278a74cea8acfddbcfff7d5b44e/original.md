```
all_variable_symbols(indp)
```

Return a vector of variable symbols in the system, including observed quantities.

For types that implement `Base.getindex` with symbolic indices using this interface, The shorthand `sys[allvariables]` can be used as shorthand for `valp[all_variable_symbols(indp)]`.

See: [`allvariables`](@ref).
