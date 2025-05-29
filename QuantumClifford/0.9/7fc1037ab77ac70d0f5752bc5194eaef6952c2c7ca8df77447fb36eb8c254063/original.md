For a not-necessarily commutative set of Paulis, return a generating set of the form ⟨A₁, A₂, ... Aₖ, Aₖ₊₁, ... Aₘ, B₁, B₂, ... Bₖ⟩ where pairs Aₖ, Bₖ anticommute and all other pairings commute. Based on [RevModPhys.87.307](@cite)

Returns the generating set as a data structure of type [`SubsystemCodeTableau`](@ref). The `logicalxview` function returns the ⟨A₁, A₂,... Aₖ⟩, and the `logicalzview` function returns ⟨B₁, B₂, ... Bₖ⟩. `stabilizerview` returns ⟨Aₖ₊₁, ... Aₘ⟩ as a Stabilizer, and `destabilizerview` returns the Destabilizer of that Stabilizer.

Phases are zeroed-out in this canonicalization.

```jldoctest
julia> canonicalize_noncomm(T"XX XZ XY")
𝒟ℯ𝓈𝓉𝒶𝒷
+ Z_
𝒳━━
+ XX
𝒮𝓉𝒶𝒷
+ X_
𝒵━━
+ XZ
```
