```
kernel_gradient( k::AbstractSPHKernel, r::T1, h_inv::T1, Δx::T2) where {T1,T2}
```

Computes the gradient of the kernel `k` at the distance `r` along the distance vector `Δx` of the neighbour `j`. 

$∇W(x_{ij}, h_i) = \frac{dW}{dx}\vert_{x_j} \frac{Δx_{ij}}{||x_{ij}||} \frac{1}{h_i}$ 
