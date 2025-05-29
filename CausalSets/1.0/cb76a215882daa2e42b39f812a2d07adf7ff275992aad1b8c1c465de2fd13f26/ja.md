```
bd_chain_coef_along(causet, i, j, dim, locality, ::Val{N}[, max_cardinality])
```

`i`から`j`までの始点と終点を持つ長さ`N+1`のすべてのチェーンのためのBenincasa-Dowkerチェーン係数の合計を返します。すなわち、`i`と`j`の間のBD^`N`演算子の係数を返します。
