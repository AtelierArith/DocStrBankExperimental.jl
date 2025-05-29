```
get_limit_cycles(
    eom::HarmonicEquation, method::SteadyStateMethod, swept, fixed, ω_lc; kwargs...)
```

ホップ周波数（通常はω*lcと呼ばれる）によって特徴付けられるリミットサイクル問題のための`get*steady_states`のバリアントです。

ω_lc = 0の解は、異なる調和変数が異なる調和に対応するという仮定に矛盾するため、非物理的とラベル付けされます。
