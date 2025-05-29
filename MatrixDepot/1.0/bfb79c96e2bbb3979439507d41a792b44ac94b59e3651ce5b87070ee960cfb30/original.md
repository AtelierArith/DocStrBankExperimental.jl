```
matrixdepot(p::Pattern, args...)
```

Return matrix according to pattern or local matrix according to name and arguments.

If not loaded, load remote matrix first. `p` must be a unique pattern (match only one name). The presence of arguments makes sense only if the pattern matches the name of a generated (=local) matrix.

Only the matrix part is delivered, also in the local cases, where the underlying function returns a structure containing matrix and vectors. Use `md = mdopen; md.A, md.b ...` to access those objects.
