```
LinearSymplecticAttentionP(sys_dim, seq_length)
```

Make an instance of `LinearSymplecticAttentionP` for a specific dimension and sequence length.

Performs: 

$$
\begin{pmatrix} Q \\ P \end{pmatrix} \mapsto \begin{pmatrix} Q \\ P + \nabla_QF \end{pmatrix},
$$

where $Q,\, P\in\mathbb{R}^{n\times{}T}$ and $F(Q) = \frac{1}{2}\mathrm{Tr}(Q A Q^T)$.

The parameters of this layer are $\bar{A} = \frac{1}{2}(A + A^T).$
