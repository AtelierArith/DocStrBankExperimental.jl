```
clebschgordan(T::Type{<:Real} = RationalRoot{BigInt}, j₁, m₁, j₂, m₂, j₃, m₃ = m₁+m₂) -> ::T
```

クレブシュ＝ゴルダン係数 <j₁, m₁; j₂, m₂ | j₃, m₃ > の値を型 `T` の実数として計算します。デフォルトでは、`T = RationalRoot{BigInt}` および `m₃ = m₁+m₂` です。

三角条件 `δ(j₁, j₂, j₃)` が満たされていない場合は `zero(T)` を返しますが、`jᵢ` と `mᵢ` が（半）整数でない場合や `abs(mᵢ) > jᵢ` の場合は `DomainError` をスローします。
