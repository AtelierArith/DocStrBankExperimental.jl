```
HubbardMom1D(address; u=1.0, t=1.0, dispersion=hubbard_dispersion)
```

Implements a one-dimensional Bose Hubbard chain in momentum space.

$$
\hat{H} =  \sum_{k} ϵ_k n_k + \frac{u}{M}\sum_{kpqr} a^†_{r} a^†_{q} a_p a_k δ_{r+q,p+k}
$$

# Arguments

  * `address`: the starting address, defines number of particles and sites.
  * `u`: the interaction parameter.
  * `t`: the hopping strength.
  * `dispersion`: defines $ϵ_k =$`dispersion(t, k)`

      * [`hubbard_dispersion`](@ref): $ϵ_k = -2(\Re(t) \cos(k) + \Im(t) \sin(k))$
      * [`continuum_dispersion`](@ref): $ϵ_k = \Re(t) k^2 - 2 \Im(t) k$

# See also

  * [`HubbardReal1D`](@ref)
  * [`ExtendedHubbardReal1D`](@ref)
