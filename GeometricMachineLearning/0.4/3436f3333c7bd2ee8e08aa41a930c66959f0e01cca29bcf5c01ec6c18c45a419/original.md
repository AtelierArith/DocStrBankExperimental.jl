```
LinearSymplecticAttentionQ(sys_dim, seq_length)
```

Make an instance of `LinearSymplecticAttentionQ` for a specific dimension and sequence length.

Performs: 

$$
\begin{pmatrix} Q \\ P \end{pmatrix} \mapsto \begin{pmatrix} Q + \nabla_PF \\ P \end{pmatrix},
$$

where $Q,\, P\in\mathbb{R}^{n\times{}T}$ and $F(P) = \frac{1}{2}\mathrm{Tr}(P A P^T)$.

The parameters of this layer are $\bar{A} = \frac{1}{2}(A + A^T).$
