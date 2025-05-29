```
logarithmic_negativity(state::GaussianState, indices::Union{Integer, AbstractVector{<:Integer}}; tola::Real = 0, tolb::Real = 128 * eps(1))
```

Calculate the logarithmic negativity of a Gaussian state partition, defined as

$$
N(\rho) = \log\|\rho^{T_B}\|_1 = - \sum_i \log(2 \tilde{v}_i^<)
$$

such that $\log$ denotes the natural logarithm, $\tilde{v}_i^<$ is the symplectic spectrum of $\mathbf{\tilde{V}}/\hbar$ which is $< 1/2$.

Therein, $\mathbf{\tilde{V}} = \mathbf{T} \mathbf{V} \mathbf{T}$ where

$$
\forall k : \mathbf{T} q_k = q_k
\forall k \in \mathrm{B} : \mathbf{T} p_k = -p_k
\forall k \notin \mathrm{B} : \mathbf{T} p_k = p_k
$$

# Arguments

  * `state`: Gaussian state whose logarithmic negativity is to be calculated.
  * `indices`: Integer or collection thereof, specifying the binary partition.
  * `tola`: Tolerance (inclusive) above the cut-off at $0$ for computing $\log(x)$.
  * `tolb`: Tolerance (inclusive) below the cut-off at $1$ for computing $\log(x)$.
