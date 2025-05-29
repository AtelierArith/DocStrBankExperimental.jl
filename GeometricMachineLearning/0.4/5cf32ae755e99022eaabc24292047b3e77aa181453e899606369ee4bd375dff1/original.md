```
GrassmannLieAlgHorMatrix(B::AbstractMatrix, N::Integer, n::Integer)
```

Build an instance of `GrassmannLieAlgHorMatrix` based on an arbitrary matrix `B` of size $(N-n)\times{}n$.

`GrassmannLieAlgHorMatrix` is the *horizontal component of the Lie algebra of skew-symmetric matrices* (with respect to the canonical metric).

# Extended help

The projection here is: $\pi:S \to SE/\sim$ where 

$$
E = \begin{bmatrix} \mathbb{I}_{n} \\ \mathbb{O}_{(N-n)\times{}n}  \end{bmatrix},
$$

and the equivalence relation is 

$$
V_1 \sim V_2 \iff \exists A\in\mathcal{S}_\mathrm{skew}(n) \text{ such that } V_2 = V_1 + \begin{bmatrix} A \\ \mathbb{O} \end{bmatrix}
$$

An element of GrassmannLieAlgMatrix takes the form: 

$$
\begin{pmatrix}
\bar{\mathbb{O}} & B^T \\ B & \mathbb{O}
\end{pmatrix},
$$

where $\bar{\mathbb{O}}\in\mathbb{R}^{n\times{}n}$ and $\mathbb{O}\in\mathbb{R}^{(N - n)\times(N-n)}.$
