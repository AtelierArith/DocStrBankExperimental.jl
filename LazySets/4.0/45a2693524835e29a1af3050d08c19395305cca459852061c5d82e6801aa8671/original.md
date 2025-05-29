```
QuadraticMap{N, S<:LazySet{N}, MVT<:AbstractVector{<:AbstractMatrix{N}}} <: LazySet{N}
```

Type that represents a quadratic map of a set.

### Fields

  * `Q` – matrices
  * `X` – set

### Notes

The quadratic map of a set $X$ given $n$ square matrices $Q^{(i)}$ is defined as

$$
\left\{ λ \mid λ_i = x^T Q^{(i)} x,~i = 1, …, n,~x ∈ X \right\}
$$

where each coordinate $i$ is influenced by the $i$-th matrix $Q^{(i)}$.
