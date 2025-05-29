```
xpnorm(
    p::Float64,
    f::Function,
    mesh::Mesh;
    qdim::Int64 = 1
) -> Float64
```

Does the same as previous `xpnorm(...)`, but takes a continous function and a mesh as arguments instead of a discrete derivative (tensor) and coefficient vector.

Requires new mandatory arguments

  * `f::Function`: Analytic description of the function to be evaluated.
  * `mesh::Mesh`: FEM mesh corresponding to $T_{h_\Omega}$.

which replace

  * `dv::AbstractDict{Tuple{Int64,Int64},AbstractVector{Float64}}`
