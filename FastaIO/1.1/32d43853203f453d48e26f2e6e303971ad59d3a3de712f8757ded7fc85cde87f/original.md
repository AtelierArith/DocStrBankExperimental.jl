```
readfasta(file::Union{String,IO}, [sequence_type::Type = String])
```

This function parses a whole FASTA file at once and stores it into memory. The result is a `Vector{Any}` whose elements are tuples consisting of `(description, sequence)`, where `description` is a `String` and `sequence` contains the sequence data, stored in a container type defined by the `sequence_type` optional argument (see [The sequence storage type](@ref) section for more information).
