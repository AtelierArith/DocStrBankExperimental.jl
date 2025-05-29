```julia
get_cycle_variables(
    eom::QuestBase.HarmonicEquation,
    ω_lc::Symbolics.Num
) -> Vector{QuestBase.HarmonicVariable}

```

`ω_lc`でラベル付けされたリミットサイクルに参加するハーモニック変数を返します。
