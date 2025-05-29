```
diff_right_compose(G::LieGroup{ℝ, AbelianMultiplicationGroupOperation, Sphere}, g, h, X)
diff_right_compose!(G::LieGroup{ℝ, AbelianMultiplicationGroupOperation, Sphere}, Y, g, h, X)
```

円群の右群乗法 $λ_g(h) = g∘h$ の微分を計算します。これは $ℝ^2$ の二次元ベクトルとして表されます。

[`AbelianMultiplicationGroupOperation`](@ref) に対しては、$Dλ_g(h)[X] = X*g$ に簡略化され、ここでの乗法は実平面を複素平面と同型にした後の複素乗法に対応します。
