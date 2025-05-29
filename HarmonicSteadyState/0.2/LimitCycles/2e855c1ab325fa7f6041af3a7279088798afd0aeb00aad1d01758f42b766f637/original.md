```julia
get_cycle_variables(
    eom::QuestBase.HarmonicEquation,
    ω_lc::Symbolics.Num
) -> Vector{QuestBase.HarmonicVariable}

```

Return the harmonic variables which participate in the limit cycle labelled by `ω_lc`.
