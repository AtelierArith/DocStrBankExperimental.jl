```
KmerFrequencySpectra{1}(freqs::Vector{MerCount{M}}, min_count::Integer = 0) where {M<:AbstractMer}
```

Build a 1 dimensional k-mer frequency spectra, from a vector of kmer counts, excluding any k-mer counts that don't meet `min_count`.
