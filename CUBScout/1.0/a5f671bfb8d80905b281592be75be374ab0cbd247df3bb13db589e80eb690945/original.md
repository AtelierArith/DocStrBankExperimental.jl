```
find_seqs(path::AbstractString, match_pattern::Regex)
find_seqs(stream::IO, match_pattern::Regex)
find_seqs(reader::FASTAReader, match_pattern::Regex)
```

Read a fasta file at `path` (or `reader` or `IO` which points to a fasta file) and query the *description* field for a given Regex `match_pattern`. These results can be supplied in either the reference tuples (for codon usage bias functions) or reference vectors (for expressivity measures).

# Examples

`jldoctest julia> find_seqs(EXAMPLE_DATA_PATH, r"ribosomal")[1:5] 5-element Vector{Bool}:  0  0  0  0  0`
