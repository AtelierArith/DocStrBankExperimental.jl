```julia
sequencing(depths, guides, samples)

```

Simulates next-gen sequencing by generating a Categorical distribution based on frequencies of each guide in each bin and then randomly samples from this distributions up to the depth provided in `depths` for each bin. Returns a dict of DataFrames with the bin names as the keys. This object can then be passed through [`Crispulator.counts_to_freqs`](@ref) followed by [`Crispulator.differences_between_bins`](@ref).
