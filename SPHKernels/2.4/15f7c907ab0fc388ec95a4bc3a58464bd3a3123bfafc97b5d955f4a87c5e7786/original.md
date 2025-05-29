```
kernel_div( k::AbstractSPHKernel, h_inv::T1, 
            xᵢ::T2, xⱼ::T2, Aⱼ::T2) where {T1,T2}
```

Compute the kernel divergence `∇⋅𝒲` between particle `i` and neighbour `j` for some SPH quantity `A`.
