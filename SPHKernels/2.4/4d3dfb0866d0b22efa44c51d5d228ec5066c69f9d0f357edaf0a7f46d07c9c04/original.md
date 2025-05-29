```
kernel_gradient( k::AbstractSPHKernel, h_inv::Real, xᵢ::T, xⱼ::T ) where T
```

Computes the gradient of the kernel `k` at the position of the neighbour `xⱼ`. 

$∇W(x_{ij}, h_i) = \frac{dW}{dx}\vert_{x_j} \frac{Δx_{ij}}{||x_{ij}||} \frac{1}{h_i}$ 
