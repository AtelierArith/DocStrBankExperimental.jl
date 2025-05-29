```
extract_parameters(m::Union{Method, Function}; parameters)
```

Extracts the intersection between the `kargs` of `m` and `parameters` (defaults to `USUAL_CONSTRAINT_PARAMETERS`).
