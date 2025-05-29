```
VariationInfo{S<:BioSequence,T<:BioSymbol}
```

Represents statistics associated with a [`SequenceVariation.Variation`](https://biojulia.dev/SequenceVariation.jl/stable/api/#SequenceVariation.Variation) within an aligned sequencing read.

# Fields

  * `variation::Variation{S,T}`: The `Variation` this object represents
  * `readpos::Float64`: The location where `variation` occurs within a sequencing read
  * `quality::Float64`: The phred-scaled basecall quality of `variation`
  * `Strand::GenomicFeatures.Strand`: Which strand `variation` appears on
