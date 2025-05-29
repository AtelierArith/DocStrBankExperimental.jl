```
output_comp_sensitivity(P,C)
```

測定ノイズ/参照からプラント出力への伝達関数。

  * "output"は、伝達関数がプラントの出力からのものであることを示します。
  * "Complimentary"は、伝達関数が出力（この場合はプラント出力）へのものであることを示します。

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

  * [`input_sensitivity`](@ref) は d₁ から e₁ への伝達関数、       (I + CP)⁻¹
  * [`output_sensitivity`](@ref) は d₂ から e₃ への伝達関数、      (I + PC)⁻¹
  * [`input_comp_sensitivity`](@ref) は d₁ から e₂ への伝達関数、  (I + CP)⁻¹CP
  * [`output_comp_sensitivity`](@ref) は d₂ から e₄ への伝達関数、 (I + PC)⁻¹PC
  * [`G_PS`](@ref) は d₁ から e₄ への伝達関数、                    (1 + PC)⁻¹P
  * [`G_CS`](@ref) は d₂ から e₂ への伝達関数、                    (1 + CP)⁻¹C
