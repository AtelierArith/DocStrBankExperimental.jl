```
parameter_refs(dref::DerivativeRef)::Tuple
```

Return the parameter references associated with the infinite derivative `dref`. This is formatted as a Tuple of containing the parameter references as they inputted to define `dref`.

**Example**

```julia-repl
julia> parameter_refs(deriv)
(t,)
```
