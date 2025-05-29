```
seqpos(v::Variation, a::Union{Alignment,AlignedSequence,PairwiseAlignment})
```

`v`の`a`の配列内での位置を取得します。

# 例

```jldoctest
using BioAlignments, BioSequences, SequenceVariation
v = Variation(dna"AAAAA", "A3T")
a = Alignment("2=1X2=", 1, 1)
seqpos(v, a)

# 出力

3
```
