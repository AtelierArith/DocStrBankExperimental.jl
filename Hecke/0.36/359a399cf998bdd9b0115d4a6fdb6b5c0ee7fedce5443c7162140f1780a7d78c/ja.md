```
ideal(O::AbsSimpleNumFieldOrder, M::ZZMatrix; check::Bool = false, M_in_hnf::Bool = false) -> AbsNumFieldOrderIdeal
```

$$
\mathcal O
$$

の基底行列$M$を持つイデアルを作成します。`check`が設定されている場合、$M$がイデアルを定義するかどうかがチェックされます（高コスト）。`M_in_hnf`が設定されている場合、$M$がすでに左下HNFにあると仮定されます。
