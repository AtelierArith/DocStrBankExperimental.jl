```
overlap_inrange(
    x::Pseudoread, y::Pseudoread, overlap_min::Integer, overlap_max::Integer
)
```

`x` と `y` の重複が `overlap_min` と `overlap_max` の範囲内であれば `true` を返し、それ以外の場合は `false` を返します。

# 例

```jldoctest
julia> using BioSequences, SequenceVariation

julia> ps1 = Pseudoread(1, 100, Haplotype(dna"A", Variation{LongDNA{4}, DNA}[]));

julia> ps2 = Pseudoread(50, 150, Haplotype(dna"A", Variation{LongDNA{4}, DNA}[]));

julia> overlap_inrange(ps1, ps2, 1, 500)
true

julia> overlap_inrange(ps1, ps2, 75, 500)
false

julia> overlap_inrange(ps1, ps2, 1, 25)
false
```
