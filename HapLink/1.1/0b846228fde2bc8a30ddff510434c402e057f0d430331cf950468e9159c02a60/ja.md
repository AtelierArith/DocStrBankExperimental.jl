```
contradicts(var::Variation{S,T}, ref::Haplotype{S,T}) where {S,T}
```

`var`が`ref`を構成する任意の`Variation`と互換性のない修正を含む場合、`true`を返します。

# 例

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
