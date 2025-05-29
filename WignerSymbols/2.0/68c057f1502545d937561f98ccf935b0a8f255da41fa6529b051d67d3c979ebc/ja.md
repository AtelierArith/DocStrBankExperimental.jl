```
racahV(T::Type{<:Real} = RationalRoot{BigInt}, j₁, j₂, j₃, m₁, m₂, m₃ = -m₁-m₂) -> ::T
```

ラカのV記号 V(j₁, j₂, j₃; m₁, m₂, m₃) = (-1)^(-j₁+j₂+j₃) * ⎛ j₁  j₂  j₃ ⎞                                                ⎝ m₁  m₂  m₃ ⎠ を型 `T` の実数として計算します。デフォルトでは、`T = RationalRoot{BigInt}` および `m₃ = -m₁-m₂` です。

三角条件 `δ(j₁, j₂, j₃)` が満たされていない場合は `zero(T)` を返しますが、`jᵢ` と `mᵢ` が（半）整数でない場合や `abs(mᵢ) > jᵢ` の場合は `DomainError` をスローします。
