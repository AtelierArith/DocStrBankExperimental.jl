```
spectra(freqs::Vector{MerCount{M}}, min_count::Integer) where {M<:AbstractMer}
```

Build a 1 dimensional kmer frequency spectra, from a vector of kmer counts, excluding any kmer counts that don't meet `min_count`.
