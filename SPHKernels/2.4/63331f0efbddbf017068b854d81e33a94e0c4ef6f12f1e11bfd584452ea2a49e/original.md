```
∇𝒲( k::AbstractSPHKernel, h_inv::Real, xᵢ::Union{Real, Vector{<:Real}}, xⱼ::Union{Real, Vector{<:Real}} )
```

Computes the gradient of the kernel `k` at the position of the neighbour `j`.  Based on Euclidean distance `r` and distance vector `Δx` between the particles.  Useful if many quantities need to be computed for the same particle pair. Compact notation of [`kernel_gradient`](@ref).

$∇W(x_{ij}, h_i) = \frac{dW}{dx}\vert_{x_j} \frac{Δx_{ij}}{||x_{ij}||} \frac{1}{h_i}$ 
