```
Haplotype{S<:BioSequence,T<:BioSymbol}
```

A set of variations within a given sequence that are all found together. Depending on the field, it might also be referred to as a "genotype" or "strain."

# Constructors

```
Haplotype(ref::S, edits::Vector{Edit{S,T}}) where {S<:BioSequence,T<:BioSymbol}
Haplotype(ref::S, vars::Vector{Variation{S,T}}) where {S<:BioSequence,T<:BioSymbol}
Haplotype(
    aln::PairwiseAlignment{T,T}
) where {T<:LongSequence{<:Union{BS.AminoAcidAlphabet,BS.NucleicAcidAlphabet}}}
```

When constructing a `Haplotype` from a vector of [`Edit`](@ref)s or [`Variation`](@ref)s, the edits are applied sequentially from first to last position, therefore the vector must always be sorted by position. These edits are sorted automatically if constructing from an alignment.
