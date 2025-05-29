```
G_CS(P, C)
```

制御信号への（-）測定ノイズまたは（+）参照からの閉ループ伝達関数。技術的には、伝達関数は `(1 + CP)⁻¹C` で与えられるため、`SC` の方がより良いが非標準的な名前になる。

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
