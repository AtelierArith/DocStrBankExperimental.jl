```
G_PS(P, C)
```

The closed-loop transfer function from load disturbance to plant output. Technically, the transfer function is given by `(1 + PC)⁻¹P` so `SP` would be a better, but nonstandard name.

```
         ▲
         │e₁
         │  ┌─────┐
d₁────+──┴──►  P  ├─────┬──►e₄
      │     └─────┘     │
      │                 │
      │     ┌─────┐    -│
 e₂◄──┴─────┤  C  ◄──┬──+───d₂
            └─────┘  │
                     │e₃
                     ▼
```

  * [`input_sensitivity`](@ref) is the transfer function from d₁ to e₁,       (I + CP)⁻¹
  * [`output_sensitivity`](@ref) is the transfer function from d₂ to e₃,      (I + PC)⁻¹
  * [`input_comp_sensitivity`](@ref) is the transfer function from d₁ to e₂,  (I + CP)⁻¹CP
  * [`output_comp_sensitivity`](@ref) is the transfer function from d₂ to e₄, (I + PC)⁻¹PC
  * [`G_PS`](@ref) is the transfer function from d₁ to e₄,                    (1 + PC)⁻¹P
  * [`G_CS`](@ref) is the transfer function from d₂ to e₂,                    (1 + CP)⁻¹C
