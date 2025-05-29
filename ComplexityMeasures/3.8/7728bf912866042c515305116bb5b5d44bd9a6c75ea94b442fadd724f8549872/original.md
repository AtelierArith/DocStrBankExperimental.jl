```
allcounts_and_outcomes(o::OutcomeSpace, x::Array_or_SSSet) → (cts::Counts{<:Integer, 1}, Ω)
```

Like [`counts_and_outcomes`](@ref), but ensures that *all* outcomes `Ωᵢ ∈ Ω`, where `Ω = outcome_space(o, x)`), are included.

Outcomes that do not occur in the data `x` get a 0 count.
