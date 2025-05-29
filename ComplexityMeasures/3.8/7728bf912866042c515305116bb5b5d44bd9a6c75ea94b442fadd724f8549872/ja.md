```
allcounts_and_outcomes(o::OutcomeSpace, x::Array_or_SSSet) → (cts::Counts{<:Integer, 1}, Ω)
```

[`counts_and_outcomes`](@ref)と同様ですが、*すべての*結果`Ωᵢ ∈ Ω`（ここで`Ω = outcome_space(o, x)`）が含まれることを保証します。

データ`x`に現れない結果は0カウントになります。
