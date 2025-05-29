```
parameter_refs(fref::ParameterFunctionRef)::Tuple
```

Return the parameter references associated with `fref`. This is formatted as a Tuple of containing the parameter references as they inputted to define `fref`.

**Example**

```julia-repl
julia> parameter_refs(p_func)
(t,)
```
