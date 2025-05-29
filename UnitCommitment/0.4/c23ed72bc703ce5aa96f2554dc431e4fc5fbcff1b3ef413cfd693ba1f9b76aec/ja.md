```
function randomize!(
    instance::UnitCommitment.UnitCommitmentInstance,
    method::XavQiuAhm2021.Randomization,
    rng = MersenneTwister(),
)::Nothing
```

XavQiuAhm2021で説明されている方法に基づいてコストと負荷をランダム化します。
