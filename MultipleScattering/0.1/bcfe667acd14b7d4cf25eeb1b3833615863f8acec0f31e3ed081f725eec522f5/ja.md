```
continuous_to_discrete_impulse(impulse::ContinuousImpulse, t_vec, ω_vec = t_to_ω(t_vec); t_shift = 0.0, ω_shift = 0.0)
```

[`DiscreteImpulse`](@ref)を返し、`impulse`をサンプリングします。信号は`t_shift`と`ω_shift`を選択することで時間と周波数でシフトできます。
