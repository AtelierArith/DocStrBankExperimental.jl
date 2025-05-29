```julia
linear_combination(basis, θ)

```

呼び出すと `linear_combination(basis, θ, x)` を計算する callable を返します。

ドメイン変換には `linear_combination(basis, θ) ∘ transformation` を使用できますが、`basis ∘ transformation` で作業する方が好まれる場合があります。
