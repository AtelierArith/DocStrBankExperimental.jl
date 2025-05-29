```
x = triu2vec(Q; rowwise = false, her = false)
```

`nxn` 配列 `Q` の上三角部分を要素数 `n(n+1)/2` の一次元列ベクトル `x` に変形します。`her = true` の場合、`Q` は対称/エルミートであると仮定されます。`x` の要素は、`rowwise = false` の場合は `Q` の上三角部分の各列の要素を積み重ねたものであり、`rowwise = true` の場合は `Q` の上三角部分の各行の要素を積み重ねたものに対応します。
