```
G_PS(P, C)
```

負荷擾乱からプラント出力への閉ループ伝達関数。技術的には、伝達関数は `(1 + PC)⁻¹P` で与えられるため、`SP` の方がより良いが非標準的な名前です。

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
