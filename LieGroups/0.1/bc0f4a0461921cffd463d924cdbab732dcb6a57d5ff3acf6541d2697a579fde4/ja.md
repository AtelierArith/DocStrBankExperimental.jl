```
diff_left_compose(G::LieGroup{𝔽,<:AbelianMultiplicationGroupOperation}, g, h, X)
diff_left_compose!(G::LieGroup{𝔽,<:AbelianMultiplicationGroupOperation}, Y, g, h, X)
```

左群乗法の微分を計算します $λ_g(h) = g∘h$。

いくつかのアーベルリー群の表現の違いにより、このメソッドは、`AbstractArray{<:Any,0}` 型の入力を持つ特定のアーベルリー群の具体的な実装をラップし、インプレース計算をサポートします。

`Y` が `mutable` であれば、`Y` のインプレースで計算できます。    
