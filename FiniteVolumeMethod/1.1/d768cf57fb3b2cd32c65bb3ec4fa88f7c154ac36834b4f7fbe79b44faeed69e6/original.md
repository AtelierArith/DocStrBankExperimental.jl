```
compute_flux(prob::AbstractFVMProblem, i, j, u, t)
```

Given an edge with indices `(i, j)`, a solution vector `u`, a current time `t`,  and a problem `prob`, computes the flux `∇⋅q(x, y, t, α, β, γ, p) ⋅ n`,  where `n` is the normal vector to the edge, `q` is the flux function from `prob`, `(x, y)` is the midpoint of the edge, `(α, β, γ)` are the shape function coefficients,  and `p` are the flux parameters from `prob`. If `prob` is an [`FVMSystem`](@ref), the returned  value is a `Tuple` for each individual flux. The normal vector `n` is a clockwise rotation of  the edge, meaning pointing right of the edge `(i, j)`.
