```
LinearSymplecticAttentionP(sys_dim, seq_length)
```

特定の次元とシーケンス長のために `LinearSymplecticAttentionP` のインスタンスを作成します。

実行内容: 

$$
\begin{pmatrix} Q \\ P \end{pmatrix} \mapsto \begin{pmatrix} Q \\ P + \nabla_QF \end{pmatrix},
$$

ここで $Q,\, P\in\mathbb{R}^{n\times{}T}$ であり、$F(Q) = \frac{1}{2}\mathrm{Tr}(Q A Q^T)$ です。

このレイヤのパラメータは $\bar{A} = \frac{1}{2}(A + A^T).$
