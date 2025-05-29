```
HubbardReal1DEP(address; u=1.0, t=1.0, v_ho=1.0)
```

Implements a one-dimensional Bose Hubbard chain in real space with external potential.

$$
\hat{H} = -t \sum_{\langle i,j\rangle} a_i^† a_j + \sum_i ϵ_i n_i
+ \frac{u}{2}\sum_i n_i (n_i-1)
$$

# Arguments

  * `address`: the starting address, defines number of particles and sites.
  * `u`: the interaction parameter.
  * `t`: the hopping strength.
  * `v_ho`: strength of the external harmonic oscillator potential $ϵ_i = v_{ho} i^2$.

The first index is `i=0` and the maximum of the potential occurs in the centre of the lattice.

# See also

  * [`HubbardReal1D`](@ref)
  * [`HubbardMom1D`](@ref)
  * [`ExtendedHubbardReal1D`](@ref)
