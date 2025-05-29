```
inner(M::Segre{ℝ, V}, p, X, Y,)
```

Inner product between two tangent vectors $X = (ν, u_1, …, u_d)$ and $Y = (ξ, v_1, …, v_d)$ at $p ≐ (λ, x_1, \dots, x_d)$. This inner product is obtained by embedding the Segre manifold in the space of tensors equipped with the Euclidean metric:

$$
    \langle X, Y \rangle_{p} = \nu \xi + \lambda^2 (\langle u_1, v_1 \rangle_{x_1} + \dots + \langle u_d, v_d \rangle_{x_d}),
$$

where $ν, ξ ∈ T_{λ} ℝ^{+} = ℝ$ and $u_i$, $v_i ∈ T_{x_i} \mathbb{S}^{n_i - 1} ⊂ ℝ^{n_i}$.
