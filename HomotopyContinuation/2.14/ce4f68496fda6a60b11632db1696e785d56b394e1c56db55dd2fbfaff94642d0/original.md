```
AffineChartHomotopy(H::AbstractHomotopy, v::PVector{T,N})
```

Given a homotopy $H(x,t): (ℙ^{m_1} × ⋯ × ℙ^{m_N}) × ℂ → ℂⁿ$ this creates a new affine homotopy $H̄$ which operates on the affine chart defined by the vector $v ∈ ℙ^{m_1} × ⋯ × ℙ^{m_N}$ and the augmented conditions $vᵀx = 1$.
