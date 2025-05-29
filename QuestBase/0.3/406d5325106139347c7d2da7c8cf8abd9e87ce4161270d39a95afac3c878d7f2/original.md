```julia
get_independent_variables(
    eom::QuestBase.HarmonicEquation
) -> Vector{Symbolics.Num}

```

Return the independent variables (typically time) of `eom`.
