```
AffineChartSystem(F::AbstractSystem, v::PVector{T,N})
```

Given a system $F(x): (ℙ^{m_1} × ⋯ × ℙ^{m_N}) → ℂⁿ$ this creates a new affine system $F′$ which operates on the affine chart defined by the vector $v ∈ ℙ^{m_1} × ⋯ × ℙ^{m_N}$ and the augmented conditions $vᵀx = 1$.
