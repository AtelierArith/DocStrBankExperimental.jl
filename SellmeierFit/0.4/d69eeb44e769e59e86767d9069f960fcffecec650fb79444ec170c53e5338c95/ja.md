```
SellmeierModel{N,T}
```

Sellmeierモデルは、Sellmeier方程式 ε(λ) = 1 + ∑ᵢ [Bᵢ λ² / (λ² - Cᵢ)] を表します。ここで、合計は `1 ≤ i ≤ N` の範囲です。

# フィールド

  * `str::SVector{N,T<:Real}`: `str[i]` はSellmeier方程式の `i` 番目の項の強度であり、Bᵢに対応します。
  * `λres::SVector{N,T<:Real}`: `λres[i]` はSellmeier方程式の `i` 番目の項の共鳴波長であり、√Cᵢに対応します。
