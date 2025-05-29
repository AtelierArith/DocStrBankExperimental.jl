```
racahW(T::Type{<:Real} = RationalRoot{BigInt}, j₁, j₂, J, j₃, J₁₂, J₂₃) -> ::T
```

ラカの W 係数 `W(j₁, j₂, J, j₃; J₁₂, J₂₃) = <(j₁,(j₂j₃)J₂₃)J | ((j₁j₂)J₁₂,j₃)J> / sqrt((2J₁₂+1)*(2J₁₃+1))` の値を型 `T` の実数として計算します。デフォルトでは、`T = RationalRoot{BigInt}` です。

三角条件 `δ(j₁, j₂, J₁₂)`, `δ(j₂, j₃, J₂₃)`, `δ(j₁, J₂₃, J)`, `δ(J₁₂, j₃, J)` のいずれかが満たされていない場合は `zero(T)` を返しますが、`jᵢ` と `J` が整数または半整数でない場合は `DomainError` をスローします。
