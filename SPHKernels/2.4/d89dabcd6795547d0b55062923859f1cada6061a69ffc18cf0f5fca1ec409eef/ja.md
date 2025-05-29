```
∇𝒜( k::AbstractSPHKernel, h_inv, xᵢ, xⱼ, Aⱼ, mⱼ, ρⱼ)
```

粒子 `j` が粒子 `i` の SPH 量 `A` の勾配に寄与する計算を行います。 [`quantity_gradient`](@ref) のコンパクトな表記。

$$
∇\vec{A}_i(x) ≈ \sum_j \frac{m_j}{\rho_j} \vec{A}_j \: ∇W(||\vec{x}_i - \vec{x}_j||, h_i)
$$
