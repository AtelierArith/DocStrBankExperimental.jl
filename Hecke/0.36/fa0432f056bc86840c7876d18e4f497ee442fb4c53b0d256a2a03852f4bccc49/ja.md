```
fractional_ideal(O::AbsNumFieldOrder, M::ZZMatrix, b::ZZRingElem; M_in_hnf::Bool = false) -> AbsNumFieldOrderFractionalIdeal
```

$$
\mathcal O
$$

の基底行列 $M/b$ を持つ分数イデアルを作成します。`M_in_hnf` が設定されている場合、$A$ はすでに下三角 HNF にあると仮定されます。
