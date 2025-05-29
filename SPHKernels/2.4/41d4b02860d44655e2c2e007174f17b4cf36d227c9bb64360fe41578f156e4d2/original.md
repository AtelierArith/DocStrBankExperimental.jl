```
kernel_value( k::AbstractSPHKernel, h_inv::Real, 
              xᵢ::Real, xⱼ::Real )
```

Computes the value of the kernel `k` at the position of the neighbour `xⱼ`. 

$W(x_i - x_j, h_i)$
