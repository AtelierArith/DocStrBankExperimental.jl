```
setlengths!(edges::Vector{Edge}, lengths::AbstractVector)
```

Assign new lengths to a vector of `edges`. Checks that the new edge lengths are non-negative or `missing` (or -1 to be interpreted as missing).
