```
LinearSymplecticAttentionQ(sys_dim, seq_length)
```

特定の次元とシーケンス長のために `LinearSymplecticAttentionQ` のインスタンスを作成します。

実行内容:

$$
\begin{pmatrix} Q \\ P \end{pmatrix} \mapsto \begin{pmatrix} Q + \nabla_PF \\ P \end{pmatrix},
$$

ここで $Q,\, P\in\mathbb{R}^{n\times{}T}$ であり、$F(P) = \frac{1}{2}\mathrm{Tr}(P A P^T)$ です。

このレイヤのパラメータは $\bar{A} = \frac{1}{2}(A + A^T).$
