See [`output_sensitivity`](@ref)

The output [sensitivity function](https://en.wikipedia.org/wiki/Sensitivity_(control_systems)) $S_o = (I + PC)^{-1}$ is the transfer function from a reference input to control error, while the input sensitivity function $S_i = (I + CP)^{-1}$ is the transfer function from a disturbance at the plant input to the total plant input. For SISO systems, input and output sensitivity functions are equal. In general, we want to minimize the sensitivity function to improve robustness and performance, but practical constraints always cause the sensitivity function to tend to 1 for high frequencies. A robust design minimizes the peak of the sensitivity function, $M_S$. The peak magnitude of $S$ is the inverse of the distance between the open-loop Nyquist curve and the critical point -1. Upper bounding the sensitivity peak $M_S$ gives lower-bounds on phase and gain margins according to

$$
ϕ_m ≥ 2\text{sin}^{-1}(\frac{1}{2M_S}), g_m ≥ \frac{M_S}{M_S-1}
$$

Generally, bounding $M_S$ is a better objective than looking at gain and phase margins due to the possibility of combined gain and pahse variations, which may lead to poor robustness despite large gain and pahse margins.

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
