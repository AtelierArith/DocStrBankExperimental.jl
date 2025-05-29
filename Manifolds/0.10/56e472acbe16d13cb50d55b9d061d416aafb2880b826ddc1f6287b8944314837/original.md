```
log(M::AbstractProjectiveSpace, p, q)
```

Compute the logarithmic map on [`AbstractProjectiveSpace`](@ref) `M`$= 𝔽ℙ^n$, i.e. the tangent vector whose corresponding [`geodesic`](@extref `ManifoldsBase.geodesic-Tuple{AbstractManifold, Any, Any}`) starting from `p` reaches `q` after time 1 on `M`. The formula reads

$$
\log_p q = (q λ - \cos θ p) \frac{θ}{\sin θ},
$$

where $θ = \arccos|⟨q, p⟩_{\mathrm{F}}|$ is the [`distance`](@ref distance(::AbstractProjectiveSpace, p, q)) between $p$ and $q$, $⟨⋅, ⋅⟩_{\mathrm{F}}$ is the Frobenius inner product, and $λ = \frac{⟨q, p⟩_{\mathrm{F}}}{|⟨q, p⟩_{\mathrm{F}}|} ∈ 𝔽$ is the unit scalar that minimizes $d_{𝔽^{n+1}}(p - q λ)$. That is, $q λ$ is the member of the equivalence class $[q]$ that is closest to $p$ in the embedding. As a result, $\exp_p \circ \log_p \colon q ↦ q λ$.

The logarithmic maps for the real [`AbstractSphere`](@ref) $𝕊^n$ and the real projective space $ℝℙ^n$ are identical when $p$ and $q$ are in the same hemisphere.
