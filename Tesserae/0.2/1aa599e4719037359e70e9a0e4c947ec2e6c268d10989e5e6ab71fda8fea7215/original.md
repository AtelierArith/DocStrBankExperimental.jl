```
@P2G_Matrix grid=>(i,j) particles=>p mpvalues=>(ip,jp) [space] begin
    equations...
end
```

Particle-to-grid transfer macro for assembling a global matrix. A typical global stiffness matrix can be assembled as follows:

```julia
@P2G_Matrix grid=>(i,j) particles=>p mpvalues=>(ip,jp) begin
    K[i,j] = @∑ ∇w[ip] ⋅ c[p] ⋅ ∇w[jp] * V[p]
end
```

where `c` and `V` denote the stiffness (symmetric fourth-order) tensor and the volume, respectively. It is recommended to create global stiffness `K` using [`create_sparse_matrix`](@ref).
