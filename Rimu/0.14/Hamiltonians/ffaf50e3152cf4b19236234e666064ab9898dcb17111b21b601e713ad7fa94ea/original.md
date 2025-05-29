```
HubbardMom1DEP(address; u=1.0, t=1.0, v_ho=1.0, dispersion=hubbard_dispersion)
```

Implements a one-dimensional Bose Hubbard chain in momentum space with harmonic external potential.

$$
Ĥ = \sum_{k} ϵ_k n_k + \frac{u}{M}\sum_{kpqr} a^†_{r} a^†_{q} a_p a_k δ_{r+q,p+k}
            + V̂_\mathrm{ho} ,
$$

where

$$
\begin{aligned}
V̂_\mathrm{ho} & = \frac{1}{M} \sum_{p,q}  \mathrm{DFT}[V_{ext}]_{p-q} \,
                    a^†_{p} a_q ,\\
V_\mathrm{ext}(x) &= v_\mathrm{ho} \,x^2 ,
\end{aligned}
$$

is an external harmonic potential in momentum space, $\mathrm{DFT}[…]_k$ is a discrete Fourier transform performed by `fft()[k%M + 1]`, and `M == num_modes(address)`.

# Arguments

  * `address`: the starting address, defines number of particles and sites.
  * `u`: the interaction parameter.
  * `t`: the hopping strength.
  * `dispersion`: defines $ϵ_k =$`dispersion(t, k)`

      * [`hubbard_dispersion`](@ref): $ϵ_k = -2[\Re(t) \cos(k) + \Im(t) \sin(k)]$
      * [`continuum_dispersion`](@ref): $ϵ_k = \Re(t) k^2 - 2 \Im(t) k$
  * `v_ho`: strength of the external harmonic oscillator potential $v_\mathrm{ho}$.

See also [`HubbardMom1D`](@ref), [`HubbardReal1DEP`](@ref), [`Transcorrelated1D`](@ref), [`Hamiltonians`](@ref).
