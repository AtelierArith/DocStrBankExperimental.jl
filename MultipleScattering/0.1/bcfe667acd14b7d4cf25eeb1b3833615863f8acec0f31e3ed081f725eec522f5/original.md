```
continuous_to_discrete_impulse(impulse::ContinuousImpulse, t_vec, ω_vec = t_to_ω(t_vec); t_shift = 0.0, ω_shift = 0.0)
```

Returns a [`DiscreteImpulse`](@ref) by sampling `impulse`. The signal can be shifted in time and frequency by choosing `t_shit` and `ω_shift`.
