[`output_comp_sensitivity`](@ref)を参照してください。

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

  * [`input_sensitivity`](@ref)はd₁からe₁への伝達関数で、       (I + CP)⁻¹
  * [`output_sensitivity`](@ref)はd₂からe₃への伝達関数で、      (I + PC)⁻¹
  * [`input_comp_sensitivity`](@ref)はd₁からe₂への伝達関数で、  (I + CP)⁻¹CP
  * [`output_comp_sensitivity`](@ref)はd₂からe₄への伝達関数で、 (I + PC)⁻¹PC
  * [`G_PS`](@ref)はd₁からe₄への伝達関数で、                    (1 + PC)⁻¹P
  * [`G_CS`](@ref)はd₂からe₂への伝達関数で、                    (1 + CP)⁻¹C
