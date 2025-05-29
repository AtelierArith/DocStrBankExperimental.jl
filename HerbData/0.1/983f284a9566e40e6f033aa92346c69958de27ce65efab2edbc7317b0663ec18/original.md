```
write_IOPexamples(filepath::AbstractString, examples::Vector{Tuple{IOExample, Any}})
```

Writes IO examples and the corresponding programs to disk by serializing them into a file using HDF5 checking for and appending the `.xiop`.
