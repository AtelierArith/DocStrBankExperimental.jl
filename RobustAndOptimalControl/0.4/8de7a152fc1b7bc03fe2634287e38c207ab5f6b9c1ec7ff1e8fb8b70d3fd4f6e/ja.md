```
add_input_integrator(sys::StateSpace, ui = 1, ϵ = 0)
```

`sys`の出力をインデックス`ui`の入力の積分で拡張します。すなわち、`y_aug = [y; ∫u[ui]]`。詳細は[`add_low_frequency_disturbance`](@ref)を参照してください。
