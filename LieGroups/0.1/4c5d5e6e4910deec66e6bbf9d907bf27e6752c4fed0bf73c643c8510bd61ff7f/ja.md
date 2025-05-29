```
diff_left_compose(::LieGroup{ℂ, AbelianMultiplicationGroupOperation, Circle{ℂ}}, g, h, X)
diff_left_compose(::LieGroup{ℂ, AbelianMultiplicationGroupOperation, Circle{ℂ}}, Y, g, h, X)
```

左群乗法の微分を計算します $λ_g(h) = g∘h$。複素円上では、微分は通常の複素乗法に簡略化されます

$$
    λ_g(h) = g ⋅ X.
$$

これは、`Y` が `mutable` であれば、`Y` の代わりに計算できます。
