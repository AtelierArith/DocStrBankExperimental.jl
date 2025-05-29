```
basis_transform(A, B)
```

非直交基底 `A` に対して、[`basis_overlap`](@ref) を介して `B` から `A` への（おそらく密な）基底変換行列を計算します：

$$
(B^HB)^{-1}B^HA
$$
