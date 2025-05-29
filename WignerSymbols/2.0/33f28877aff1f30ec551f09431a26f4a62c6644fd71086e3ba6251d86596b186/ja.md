```
wigner6j(T::Type{<:Real} = RationalRoot{BigInt}, j₁, j₂, j₃, j₄, j₅, j₆) -> ::T
```

Wigner-6j記号 *⎧ j₁  j₂  j₃ ⎫*      ⎩ j₄  j₅  j₆ ⎭ の値を型 `T` の実数として計算します。デフォルトでは、`T = RationalRoot{BigInt}` です。

三角条件 `δ(j₁, j₂, j₃)`, `δ(j₁, j₆, j₅)`, `δ(j₂, j₄, j₆)`, `δ(j₃, j₄, j₅)` が満たされない場合は `zero(T)` を返しますが、`jᵢ` が整数または半整数でない場合は `DomainError` をスローします。
