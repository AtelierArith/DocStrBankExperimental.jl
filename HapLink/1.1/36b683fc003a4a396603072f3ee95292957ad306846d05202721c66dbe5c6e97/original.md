```
HaplotypeCall(
    haplotype::Haplotype{S,T}, reads::AbstractArray{Haplotype{S,T}}
) where {S<:BioSequence,T<:BioSymbol}
HaplotypeCall(
    haplotype::AbstractArray{Variation{S,T}}, reads::AbstractArray{Haplotype{S,T}}
) where {S<:BioSequence,T<:BioSymbol}
```

Calls haplotypes by calculating the linkage disequilibrium of `haplotype` within `reads`
