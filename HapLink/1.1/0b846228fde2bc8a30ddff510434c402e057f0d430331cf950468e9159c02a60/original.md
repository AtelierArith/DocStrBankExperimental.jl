```
contradicts(var::Variation{S,T}, ref::Haplotype{S,T}) where {S,T}
```

Returns `true` if `var` contains a modification incompatible with any of the `Variation`s that make up `ref`.

# Example

```jldoctest
julia> using BioSequences, SequenceVariation

julia> ref = Haplotype(dna"GATTACA", [Variation(dna"GATTACA", "A2T"), Variation(dna"GATTACA", "Δ5-6")]);

julia> contradicts(Variation(dna"GATTACA", "A2C"), ref)
true

julia> contradicts(Variation(dna"GATTACA", "T4A"), ref)
false

julia> contradicts(Variation(dna"GATTACA", "Δ2-2"), ref)
true

julia> contradicts(Variation(dna"GATTACA", "Δ4-4"), ref)
false

julia> contradicts(Variation(dna"GATTACA", "2G"), ref)
false

julia> contradicts(Variation(dna"GATTACA", "4G"), ref)
false
```
