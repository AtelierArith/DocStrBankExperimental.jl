```
make_causal_mask(x, dims=2)
```

同じ型のブールの正方行列 `m` を返し、そのサイズは `size(x, dims)` です。要素は `m[i, j] == i ≤ j` となるように設定されています。

[`dot_product_attention`](@ref) の注意スコアをマスクするために使用できます。
