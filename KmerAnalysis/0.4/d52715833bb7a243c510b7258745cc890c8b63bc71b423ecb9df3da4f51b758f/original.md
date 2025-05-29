```
KmerFrequencySpectra{2}(xfreqs::Vector{MerCount{M}}, yfreqs::Vector{MerCount{M}}, min_count::Integer = 0) where {M<:AbstractMer}
```

Build a 2 dimensional k-mer frequency spectra, from two vectors of kmer counts, excluding any k-mer counts that don't meet the `min_count`.

!!! tip
    Typically, `xfreqs` should be counts from a big dataset, typically something like raw reads, and `yfreqs` should be counts from a smaller or more collapsed sequence dataset like a reference genome or genome assembly graph.

    If you are comparring two similar sized datasets like two read datasets, then which one is passed as `xfreqs` and which is passed as `yfreqs` does not really matter.

