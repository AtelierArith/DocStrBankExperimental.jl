```
overapproximate(lm::LinearMap{N, <:AbstractZonotope, NM,
                              <:AbstractIntervalMatrix{NM}},
                ::Type{<:Zonotope}) where {N, NM}
```

Overapproximate an interval-matrix linear map of a zonotopic set by a zonotope.

### Input

  * `lm`       – interval-matrix linear map of a zonotopic set
  * `Zonotope` – target set type

### Output

A zonotope overapproximating the linear map.

### Algorithm

This implementation uses the method proposed in [AlthoffSB07](@citet).

Given an interval matrix $M = \tilde{M} + ⟨-\hat{M},\hat{M}⟩$ (split into a conventional matrix and a symmetric interval matrix) and a zonotope $⟨c, g_1, …, g_m⟩$, we compute the resulting zonotope $⟨\tilde{M}c, \tilde{M}g_1, …, \tilde{M}g_m, v_1, …, v_n⟩$ where the $v_j$, $j = 1, …, n$, are defined as

$$
    v_j = \begin{cases} 0 & i ≠ j \\
          \hat{M}_j (|c| + ∑_{k=1}^m |g_k|) & i = j. \end{cases}
$$
