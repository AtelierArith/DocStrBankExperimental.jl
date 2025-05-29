```
get_reference(ref_fasta)
```

Takes a path to a reference fasta. Returns a `Vector{LongDNA{4}}` of reference sequences  and a matrix taxonomic classifications. The reference fasta must be a DADA2-formatted reference database.  See [here](https://benjjneb.github.io/dada2/training.html) for examples.
