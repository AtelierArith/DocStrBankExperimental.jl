```
sigs = signatures_at(filename, line)
```

Return the signatures of all methods whose definition spans the specified location. Prior to Julia 1.5, `line` must correspond to a line in the method body (not the signature or final `end`).

Returns `nothing` if there are no methods at that location.
