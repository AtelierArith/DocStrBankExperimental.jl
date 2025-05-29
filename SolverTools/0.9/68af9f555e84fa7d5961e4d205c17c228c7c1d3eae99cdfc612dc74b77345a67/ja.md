```
active!(indices, x, ℓ, u; rtol = 1e-8, atol = 1e-8)
```

xにおけるアクティブ境界の`BitVector`を更新します。許容誤差は`min(rtol * (uᵢ-ℓᵢ), atol)`を使用します。もしℓᵢまたはuᵢが有限でない場合、`atol`のみが使用されます。
