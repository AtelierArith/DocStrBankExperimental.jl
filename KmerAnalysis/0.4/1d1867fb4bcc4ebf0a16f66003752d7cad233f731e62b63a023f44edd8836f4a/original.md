```
spectra(x::Pair{I,C}, min_count::Integer = 0) where {I,C<:AbstractKmerCounter}
```

Build a 1 dimensional kmer frequency spectra, using a pair of (input data => kmer counter) as the input argument `x`. The spectra function uses the kmer counter to get the counts from the input data, before computing the spectra.

Any kmer counts that don't meet `min_count` are excluded.
