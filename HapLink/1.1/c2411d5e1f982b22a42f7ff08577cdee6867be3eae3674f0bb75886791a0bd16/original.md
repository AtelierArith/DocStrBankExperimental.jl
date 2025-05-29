```
VariationPileup
```

Summarizes the basecalls that support a `Variation` within a set of alignments.

# Fields

  * `variation::Variation`: The Variation of this pileup entry
  * `depth::UInt`: The number of times the position of `variation` appears in this set of alignments
  * `readpos::Vector{Float64}`: The relative positions of `variation` within each read
  * `quality::Vector{Float64}`: The phred quality of `variation` within each read
  * `strand::Vector{Strand}`: Which strand each `variation` is found on
