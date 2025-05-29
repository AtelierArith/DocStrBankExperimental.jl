```
walkpath(g, paths, start; dir=:out, stopcond=(g,v)->false)
```

Walk on the given `paths` starting from `start` and return the last nodes. If `dir` is specified, use the corresponding edge direction (`:in` and `:out` are acceptable values).
