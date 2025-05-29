```
is_choi_matrix(
    Λ :: AbstractMatrix,
    dims :: Vector{Int};
    atol=ATOL :: Float
) :: Bool
```

Returns `true` if matrix `Λ` is a Choi operator representation of a quantum channel.

The requirements on `Λ` are ([https://arxiv.org/abs/1111.6950](https://arxiv.org/abs/1111.6950)):

  * Is Hermitian, $\Lambda = \Lambda^{\dagger}$.
  * Is trace-preserving, $\text{Tr}_B[\Lambda^{AB}]=\mathbb{I}_A$.
  * Is completely-positive, $\Lambda \geq 0$.
