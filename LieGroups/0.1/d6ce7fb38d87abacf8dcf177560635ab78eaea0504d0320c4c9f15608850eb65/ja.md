```
diff_right_compose(::LieGroup{ℂ, AbelianMultiplicationGroupOperation, Circle{ℂ}}, g, h, X)
diff_right_compose(::LieGroup{ℂ, AbelianMultiplicationGroupOperation, Circle{ℂ}}, Y, g, h, X)
```

右群乗法の微分を計算します $ρ_g(h) = h∘g$。複素円上では、微分は通常の複素乗法に簡略化されます

$$
    ρ_g(h) = X ⋅ g.
$$

これは、[`AbelianMultiplicationGroupOperation`](@ref)で定義されたラッパーのため、`Y`が`mutable`であれば`Y`のインプレースで計算できます。
