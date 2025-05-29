```
Haplotype{S<:BioSequence,T<:BioSymbol}
```

与えられた配列内のすべての変異のセット。分野によっては、「遺伝子型」や「株」と呼ばれることもあります。

# コンストラクタ

```
Haplotype(ref::S, edits::Vector{Edit{S,T}}) where {S<:BioSequence,T<:BioSymbol}
Haplotype(ref::S, vars::Vector{Variation{S,T}}) where {S<:BioSequence,T<:BioSymbol}
Haplotype(
    aln::PairwiseAlignment{T,T}
) where {T<:LongSequence{<:Union{BS.AminoAcidAlphabet,BS.NucleicAcidAlphabet}}}
```

[`Edit`](@ref)s または [`Variation`](@ref)s のベクターから `Haplotype` を構築する際、編集は最初から最後の位置まで順次適用されるため、ベクターは常に位置でソートされている必要があります。アライメントから構築する場合、これらの編集は自動的にソートされます。
