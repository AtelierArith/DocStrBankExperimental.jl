```
mj_fullM(m, dst, M)
```

Convert sparse inertia matrix M into full (i.e. dense) matrix.

# Arguments

  * **`m::Model`** -> Constant.
  * **`dst::Matrix{Float64}`** -> A matrix of variable size. `dst` should be of shape (nv, nv).
  * **`M::Vector{Float64}`** -> A vector of variable size. `M` should be a vector, not a matrix. `M` should be of size nM. Constant.
