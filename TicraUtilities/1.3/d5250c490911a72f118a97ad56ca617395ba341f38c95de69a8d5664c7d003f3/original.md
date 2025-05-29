```
read_cutfile(fname) -> Vector{Cut}
```

Read data from a possibly multi-frequency Ticra-compatible cut file.  

Return a single `Cut` struct or a vector `Cut` structs.  Each element of the returned vector  corresponds to a particular operating frequency partition in the file.  If there  is only a single partition in the file, then instead of returning a 1-element vector, the single object of type `Cut` is returned as a scalar.
