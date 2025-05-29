```
fractional_ideal(O::RelNumFieldOrder, M::PMat; M_in_hnf::Bool = false) -> RelNumFieldOrderFractionalIdeal
```

$$
\mathcal O
$$

の基底擬似行列$M$を持つ分数イデアルを作成します。`M_in_hnf`が設定されている場合、$M$はすでに下三角擬似HNFにあると仮定されます。
