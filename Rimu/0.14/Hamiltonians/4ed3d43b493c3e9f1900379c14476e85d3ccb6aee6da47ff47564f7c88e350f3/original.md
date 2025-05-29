```
ExtendedHubbardMom1D(
    address; 
    u=1.0, t=1.0, v=1.0, dispersion=hubbard_dispersion, boundary_condition = 0.0
)
```

Implements a one-dimensional extended Hubbard chain, also known as the $t - V$ model,  in momentum space.

$$
\hat{H} =  \sum_{k} ϵ_k n_k + \frac{1}{2M} \sum_{kpqr} (u + 2v \cos(q-p)) a^†_{r} a^†_{q} a_p a_k δ_{r+q,p+k}
$$

# Arguments

  * `address`: the starting address, defines number of particles and sites.
  * `u`: the interaction parameter.
  * `t`: the hopping strength.
  * `boundary_condition`: `θ <: Number`: hopping over the boundary incurs a   factor $\exp(iθ)$ for a hop to the right and $\exp(−iθ)$ for a hop to the left.
  * `dispersion`: defines $ϵ_k =$`dispersion(t, k + θ)`

      * [`hubbard_dispersion`](@ref): $ϵ_k = -2 (\Re(t) \cos(k + θ) + \Im(t) \sin(k + θ))$
      * [`continuum_dispersion`](@ref): $ϵ_k = \Re(t) (k + θ)^2 - 2 \Im(t) (k + θ)$

# See also

  * [`HubbardMom1D`](@ref)
  * [`HubbardReal1D`](@ref)
  * [`ExtendedHubbardReal1D`](@ref)
