```
kernel_value( k::AbstractSPHKernel, h_inv::T1, 
                   xᵢ::T2, xⱼ::T2 ) where {T1,T2}
```

Computes the value of the kernel `k` at the position of the neighbour `xⱼ`. 

$W(\vec{x}_i - \vec{x}_j, h_i)$
