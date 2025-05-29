```
translate(hap::Haplotype{S,T}, aln::PairwiseAlignment{S,S}) where {S,T}
```

Convert the variations in `hap` to a new reference sequence based upon `aln`. The alignment rules follow the conventions of [`translate(::Variation, PairwiseAlignment)`](@ref translate(::Variation{S,T}, ::PairwiseAlignment{S,S}) where {S,T}). Indels at the beginning or end may not be preserved. Returns a new [`Haplotype`](@ref)
