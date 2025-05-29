```
overlap_inrange(
    x::Pseudoread, y::Pseudoread, overlap_min::Integer, overlap_max::Integer
)
```

Returns `true` if the overlap between `x` and `y` is within `overlap_min` and `overlap_max`, returns `false` otherwise

# Example

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
