```
seqpos(v::Variation, a::Union{Alignment,AlignedSequence,PairwiseAlignment})
```

Get the position of `v` in the sequence of `a`.

# Example

```jldoctest
using BioAlignments, BioSequences, SequenceVariation
v = Variation(dna"AAAAA", "A3T")
a = Alignment("2=1X2=", 1, 1)
seqpos(v, a)

# output

3
```
