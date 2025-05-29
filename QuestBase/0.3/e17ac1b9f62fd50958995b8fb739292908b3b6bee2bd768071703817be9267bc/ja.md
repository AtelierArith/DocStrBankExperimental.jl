```julia
rearrange_standard(
    eom::QuestBase.HarmonicEquation
) -> QuestBase.HarmonicEquation

```

`eom`を標準形に再配置し、変数の導関数が一方の側にあるようにします。
