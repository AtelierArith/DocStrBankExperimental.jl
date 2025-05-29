```
∇dot𝒲( k::AbstractSPHKernel, h_inv::T1, xᵢ::T2, xⱼ::T2, Aⱼ::T2) where {T1,T2}
```

粒子 `i` と隣接粒子 `j` の間のカーネル発散 `∇⋅𝒲` を、ある SPH 量 `A` に対して計算します。 [`kernel_div`](@ref) のコンパクトな表記。
