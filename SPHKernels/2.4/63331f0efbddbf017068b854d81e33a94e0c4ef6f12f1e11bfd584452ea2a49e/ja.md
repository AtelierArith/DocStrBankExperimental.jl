```
∇𝒲( k::AbstractSPHKernel, h_inv::Real, xᵢ::Union{Real, Vector{<:Real}}, xⱼ::Union{Real, Vector{<:Real}} )
```

隣接粒子 `j` の位置でのカーネル `k` の勾配を計算します。粒子間のユークリッド距離 `r` と距離ベクトル `Δx` に基づいています。同じ粒子ペアに対して多くの量を計算する必要がある場合に便利です。 [`kernel_gradient`](@ref) の簡潔な表記。

$$
∇W(x_{ij}, h_i) = \frac{dW}{dx}\vert_{x_j} \frac{Δx_{ij}}{||x_{ij}||} \frac{1}{h_i}
$$
