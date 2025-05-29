```
continuous_chain_ratio(dim, k) -> Floa64
```

Calculate the predicted continuum limit of the chain relation ratio $\langle \mathbf{C_k} \rangle / n^k$ for dimension `dim`, where $C_k$ is the number of strictly ascending chains with length `k` as calculated by [`count_relations`](@ref), and $n$ is the number of atoms in the causet.

The predicted continuum limit is:

$$
\frac{\langle \mathbf{C_k} \rangle}{n^k} = \frac{1}{k} \left( \frac{Γ(d+1)}{2} \right)^{k-1} \frac{Γ(d/2) Γ(d)}{Γ(kd/2) Γ((k+1)d/2)}
$$

For `k = 2`, this is equal to [`continuous_relation_ratio`](@ref).
