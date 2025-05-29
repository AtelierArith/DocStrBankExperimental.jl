```
criterion_and_gradient!(∇Q::Union{AbstractMatrix{<:Real}, Nothing},
                        method::RotationMethod, Λ::AbstractMatrix{<:Real})
```

与えられた `method` に対して、因子負荷行列 `Λ` に関する品質基準 *Q* とその勾配を計算します。勾配は `∇Q` 行列に出力され、これは `Λ` と同じ次元を持つ必要があります。`∇Q ≡ nothing` の場合、`∇Q` の計算はスキップされます。

*Q* 基準値を返します。
