```
∇𝒲( k::AbstractSPHKernel, h_inv::T1, xᵢ::T2, xⱼ::T2 ) where {T1<:Real,T2}
```

Computes the gradient of the kernel `k` at the position of the neighbour `xⱼ`.  Compact notation of [`kernel_gradient`](@ref).

$∇W(x_{ij}, h_i) = \frac{dW}{dx}\vert_{x_j} \frac{Δx_{ij}}{||x_{ij}||} \frac{1}{h_i}$ 
