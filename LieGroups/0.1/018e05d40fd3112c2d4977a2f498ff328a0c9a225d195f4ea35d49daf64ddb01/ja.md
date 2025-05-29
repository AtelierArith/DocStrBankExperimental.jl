```
diff_left_compose(G::LieGroup{ℝ, AbelianMultiplicationGroupOperation, Sphere}, g, h, X)
diff_left_compose!(G::LieGroup{ℝ, AbelianMultiplicationGroupOperation, Sphere}, Y, g, h, X)
```

円周群の左群乗法 $λ_g(h) = g∘h$ の微分を計算します。これは $ℝ^2$ の二次元ベクトルとして表されます。

[`AbelianMultiplicationGroupOperation`](@ref) の場合、これは $Dλ_g(h)[X] = g*X$ に簡略化され、乗法は実平面を複素平面と同型にした後の複素乗法に対応します。

これは `Y` のインプレースで計算できます。
