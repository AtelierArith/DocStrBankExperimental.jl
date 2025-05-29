```
output_sensitivity(P, C)
```

測定ノイズ/参照から制御誤差への伝達関数。

  * "output"は、植物の出力からの伝達関数を示します。

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

  * [`input_sensitivity`](@ref) は d₁ から e₁ への伝達関数で、       (I + CP)⁻¹
  * [`output_sensitivity`](@ref) は d₂ から e₃ への伝達関数で、      (I + PC)⁻¹
  * [`input_comp_sensitivity`](@ref) は d₁ から e₂ への伝達関数で、  (I + CP)⁻¹CP
  * [`output_comp_sensitivity`](@ref) は d₂ から e₄ への伝達関数で、 (I + PC)⁻¹PC
  * [`G_PS`](@ref) は d₁ から e₄ への伝達関数で、                    (1 + PC)⁻¹P
  * [`G_CS`](@ref) は d₂ から e₂ への伝達関数で、                    (1 + CP)⁻¹C
