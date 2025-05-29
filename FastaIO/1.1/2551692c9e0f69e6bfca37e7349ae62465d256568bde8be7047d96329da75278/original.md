```
FastaReader{T}(file::Union{AbstractString,IO})
```

This creates an object which is able to parse FASTA files, one entry at a time. `file` can be a plain text file or a gzip-compressed file (it will be autodetected from the content). The type `T` determines the output type of the sequences (see [The sequence storage type](@ref) section for more information) and it defaults to `String`.

The data can be read out by iterating the `FastaReader` object:

```julia
for (name, seq) in FastaReader("somefile.fasta")
    # do something with name and seq
end
```

As shown, the iterator returns a tuple containing the description (always a `String`) and the data (whose type is set when creating the `FastaReader` object (e.g. `FastaReader{Vector{UInt8}}(filename)`).

The `FastaReader` type has a field `num_parsed` which contains the number of entries parsed so far.

Other ways to read out the data are via the [`readentry`](@ref) and [`readfasta`](@ref) functions.
