```
ideal(O::RelNumFieldOrder, M::PMat; check::Bool = true, M_in_hnf::Bool = false) -> RelNumFieldOrderIdeal
```

$$
\mathcal O
$$

の基底擬似行列$M$のイデアルを作成します。`check`が設定されている場合、$M$がイデアルを定義するかどうかがチェックされます。`M_in_hnf`が設定されている場合、$M$はすでに下左擬似HNFにあると仮定されます。
