```
Q = vec2triu(x; rowwise = false, her = false)
```

1次元の列ベクトル `x` から `n(n+1)/2` 要素を持つ `nxn` 上三角行列 `Q` を構築します。`her = false` の場合は上三角行列、`her = true` の場合は `nxn` 対称/エルミート配列 `Q` になります。`x` の要素は、`rowwise = false` の場合は `Q` の上三角部分の各列の要素を積み重ねたものであり、`rowwise = true` の場合は `Q` の上三角部分の各行の要素を積み重ねたものです。
