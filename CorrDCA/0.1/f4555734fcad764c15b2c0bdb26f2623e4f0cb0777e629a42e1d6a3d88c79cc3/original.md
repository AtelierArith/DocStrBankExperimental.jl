```
read_fasta_alignment(filename::AbstractString, max_gap_fraction::Real)
```

Return a `L × M` matrix of integers (`L` is the sequence length, and `M` is the number of sequences) of the  multiple sequence alignment contained in the fasta file `filename` including all sequences with a fraction of gaps (`-`) ≤  `max_gap_fraction`.
