```
zj = ZudkevitchJoffe(; F_a = (T, c_i) -> 1.0, F_b = (T, c_i) -> 1.0)
```

Specializes the GenericCubicEOS to the Zudkevitch-Joffe cubic equation of state.

The Zudkevitch-Joffe equations of state allows for per-component functions of  temperature that modify the `weight_ai` and `weight_bi` functions. These additional fitting parameters allows for more flexibility when matching complex mixtures.
