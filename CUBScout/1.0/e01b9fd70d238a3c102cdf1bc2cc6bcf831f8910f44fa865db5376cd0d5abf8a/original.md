```
seq_names(path::AbstractString)
seq_names(reader::FASTAReader)
seq_names(stream::IO)
```

Read a fasta file at `path` and return the *name* fields. Just adds convenience on top of FASTX functions.

# Examples

```jldoctest
julia> seq_name_vector = seq_names(EXAMPLE_DATA_PATH);

julia> seq_name_vector[1]
"lcl|NC_000964.3_cds_NP_387882.1_1"
```
