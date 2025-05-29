```
wigner3j(T::Type{<:Real} = RationalRoot{BigInt}, j₁, j₂, j₃, m₁, m₂, m₃ = -m₂-m₁) -> ::T
```

Wigner-3j記号の値を計算します     ⎛ j₁  j₂  j₃ ⎞     ⎝ m₁  m₂  m₃ ⎠ を型 `T` の実数として。デフォルトでは、`T = RationalRoot{BigInt}` および `m₃ = -m₁-m₂` です。

三角条件 `δ(j₁, j₂, j₃)` が満たされていない場合は `zero(T)` を返しますが、`jᵢ` と `mᵢ` が（半）整数でない場合や `abs(mᵢ) > jᵢ` の場合は `DomainError` をスローします。
