```
perturbationgrowth([p,] bd, t) -> ts, Rs, is
```

Calculate the evolution of the perturbation vector `Δ` along the trajectory of `p` in `bd` for total time `t`. `Δ` is initialised as `[1,1,1,1]`.

If a particle is not given, a random one is picked through [`randominside`](@ref). Returns empty lists for pinned particles.

## Description

This function *safely* computes the time evolution of a perturbation vector using the linearized dynamics of the system, as outlined by [1]. Because the dynamics are linear, we can safely re-normalize the perturbation vector after every collision (otherwise the perturbations grow to infinity).

Immediately before *and after* every collison, this function computes

  * the current time.
  * the element-wise ratio of Δ with its previous value
  * the obstacle index of the current obstacle

and returns these in three vectors `ts, Rs, is`.

To obtain the *actual* evolution of the perturbation vector you can use the function `perturbationevolution(Rs)` which simply does

```julia
Δ = Vector{SVector{4,Float64}}(undef, length(R))
Δ[1] = R[1]
for i in 2:length(R)
    Δ[i] = R[i] .* Δ[i-1]
end
```

[1] : Ch. Dellago *et al*, [Phys. Rev. E **53** (1996)](http://link.aps.org/doi/10.1103/PhysRevE.53.1485)
