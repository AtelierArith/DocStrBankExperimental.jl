```julia
InfRational(A, L)

```

ドメインは $y = A + L ⋅ x / √(1 - x^2)$ を使用して `(-Inf, Inf)` に変換され、`L > 0` です。

# 例のマッピング (ドメイン $(-1,1)$ の場合)

  * $$
    0 ↦ A
    $$
  * $$
    ±0.5 ↦ A ± L / √3
    $$
