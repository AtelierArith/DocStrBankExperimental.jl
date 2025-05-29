```
ideal(O::AbsSimpleNumFieldOrder, M::ZZMatrix; check::Bool = false, M_in_hnf::Bool = false) -> AbsNumFieldOrderIdeal
```

$$
\mathcal O
$$

の理想を基底行列$M$で作成します。`check`が設定されている場合、$M$が理想を定義しているかどうかがチェックされます（高コスト）。`M_in_hnf`が設定されている場合、$M$がすでに下三角HNFであると仮定されます。
