```
Δ(T::Type{<:Real} = RationalRoot{BigInt}, j₁, j₂, j₃) -> ::T
```

三角係数 `Δ(j₁, j₂, j₃) = √((j₁+j₂-j₃)!*(j₁-j₂+j₃)!*(j₂+j₃-j₁)! / (j₁+j₂+j₃+1)!)` を型 `T` の実数として計算します。

三角条件 `δ(j₁, j₂, j₃)` が満たされていない場合は `zero(T)` を返しますが、`jᵢ` が（半）整数でない場合は `DomainError` をスローします。
