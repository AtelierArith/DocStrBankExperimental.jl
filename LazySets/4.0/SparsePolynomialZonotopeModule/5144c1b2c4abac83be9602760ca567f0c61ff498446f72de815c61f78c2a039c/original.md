```
SparsePolynomialZonotope{N, VN<:AbstractVector{N}, MN<:AbstractMatrix{N},
                         MNI<:AbstractMatrix{N},
                         ME<:AbstractMatrix{Int},
                         VI<:AbstractVector{Int}}
    <: AbstractSparsePolynomialZonotope{N}
```

Type that represents a sparse polynomial zonotope.

A sparse polynomial zonotope $\mathcal{PZ} ⊂ ℝ^n$ is represented by the set

$$
\mathcal{PZ} = \left\{x ∈ ℝ^n : x = c + ∑ᵢ₌₁ʰ\left(∏ₖ₌₁ᵖ α_k^{E_{k, i}} \right)Gᵢ+∑ⱼ₌₁^qβⱼGIⱼ,~~ α_k, βⱼ ∈ [-1, 1],~~ ∀ k = 1,…,p, j=1,…,q \right\},
$$

where $c ∈ ℝ^n$ is the offset vector (or center), $Gᵢ ∈ ℝ^{n}$ are the dependent generators, $GIⱼ ∈ ℝ^{n}$ are the independent generators, and $E ∈ \mathbb{N}^{p×h}_{≥0}$ is the exponent matrix with matrix elements $E_{k, i}$.

In the implementation, $Gᵢ ∈ ℝ^n$ are arranged as columns of the dependent generator matrix $G ∈ ℝ^{n × h}$, and similarly $GIⱼ ∈ ℝ^{n}$ are arranged as columns of the independent generator matrix $GI ∈ ℝ^{n×q}$.

The shorthand notation $\mathcal{PZ} = ⟨ c, G, GI, E, idx ⟩$ is often used, where $idx ∈ \mathbb{N}^p$ is a list of non-repeated natural numbers storing a unique identifier for each dependent factor $αₖ$.

### Fields

  * `c`   – offset vector
  * `G`   – dependent generator matrix
  * `GI`  – independent generator matrix
  * `E`   – exponent matrix
  * `idx` – identifier vector of positive integers for the dependent parameters

### Notes

Sparse polynomial zonotopes were introduced in [KochdumperA21](@citet).
