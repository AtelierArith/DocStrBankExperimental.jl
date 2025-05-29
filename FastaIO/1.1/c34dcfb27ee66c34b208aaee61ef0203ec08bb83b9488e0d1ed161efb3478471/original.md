```
writefasta(filename::String, data, [mode::String = "w"]; check_description=true)
```

This function dumps data to a FASTA file, auto-formatting it so to follow the specifications detailed in the section titled [The FASTA format](@ref). The `data` can be anything which is iterable and which produces `(description, sequence)` tuples upon iteration, where the `description` must be convertible to a `String` and the `sequence` can be any iterable object which yields elements convertible to ASCII characters (e.g. a `String`, a `Vector{UInt8}` etc.).

Examples:

```julia
writefasta("somefile.fasta", [("GENE1", "GCATT"), ("GENE2", "ATTAGC")])
writefasta("somefile.fasta", ["GENE1" => "GCATT", "GENE2" => "ATTAGC"])
```

If the `filename` ends with `.gz`, the result will be a gzip-compressed file.

The `mode` flag determines how the `filename` is open; use `"a"` to append the data to an existing file.

Set the keyword `check_description=false` to disable the warning message given when description lines are too long.
