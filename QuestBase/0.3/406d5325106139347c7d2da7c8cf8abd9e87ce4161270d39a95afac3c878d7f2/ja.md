```julia
get_independent_variables(
    eom::QuestBase.HarmonicEquation
) -> Vector{Symbolics.Num}

```

`eom`の独立変数（通常は時間）を返します。
