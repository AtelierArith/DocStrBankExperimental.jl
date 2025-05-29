```
compute_flux_function(b::AbstractArray{T,N}, Δ::Vector{T}, nG::Int=2) where {T,N}
```

Calculate the 2D magnetic flux function ψ from the magnetic field `b` and discrete steps `Δ`. `nG` is the number of ghost cells along each dimension in the vector field. ψ is defined as $\psi = \int B_x dz = - \int B_z dx$ from $\mathbf{B} = \hat{y}\times\nabla\psi$ in the X-Z plane and Y is the out-of-plane direction. This is strictly true if B is divergence-free and the guide field By is constant. However, numerically there will be errors. The current implementation calculates ψ by integrating along -z boundary first, and then going along z. Reference: [Flux function](https://doi.org/10.1063/1.3657424)
