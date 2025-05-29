```
serialize(filename::AbstractString, structures::AbstractVector{<:ProteinStructure})
```

Serialize a vector of `ProteinStructure` objects to a JLD2 file. This function creates a new `ProteinStructureStore` and writes each structure in the input vector to it. Each structure is stored using its name as the key.
