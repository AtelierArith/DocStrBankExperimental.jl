```
variable_symbols(indp, [i])
```

Return a vector of the symbolic variables being solved for in the index provider `indp`. If `constant_structure(sys) == false` this accepts an additional parameter indicating the current time index. The returned vector should not be mutated.

For types that implement `Base.getindex` with symbolic indices using this interface, the shorthand `valp[solvedvariables]` can be used as shorthand for `valp[variable_symbols(sys)]`. See: [`solvedvariables`](@ref).
