```
FileIO.save(file, uf::T; compress=false) where {T<:UnfoldModel}
```

Save UnfoldModel in a (by default uncompressed) .jld2 file.

For memory efficiency the designmatrix is set to missing. If needed, it can be reconstructed when loading the model.
