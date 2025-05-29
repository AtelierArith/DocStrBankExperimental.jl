```
∇𝒲( k::AbstractSPHKernel, h_inv::T1, xᵢ::T2, xⱼ::T2 ) where {T1<:Real,T2}

カーネル `k` の勾配を隣接点 `xⱼ` の位置で計算します。 [`kernel_gradient`](@ref) のコンパクトな表記です。

$∇W(x_{ij}, h_i) = \frac{dW}{dx}\vert_{x_j} \frac{Δx_{ij}}{||x_{ij}||} \frac{1}{h_i}$ 
```
