```
write_IOexamples(filepath::AbstractString, examples::Vector{IOExample})
```

Writes IO examples to disk by serializing them into a file using HDF5 checking for and appending the `.xio` file ending.
