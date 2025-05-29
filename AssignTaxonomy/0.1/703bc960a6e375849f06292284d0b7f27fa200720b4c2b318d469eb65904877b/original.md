```
get_targets(seq_fasta)
```

Takes a path to a fasta of sequences to be classified. Returns a `Vector{LongDNA{4}}` of target sequences  and a `Vector{String}` of sequence IDs, taken from hte fasta record identifiers.
