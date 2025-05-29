```
HubbardReal1D(address; u=1.0, t=1.0)
```

Implements a one-dimensional Bose Hubbard chain in real space.

$$
\hat{H} = -t \sum_{\langle i,j\rangle} a_i^† a_j + \frac{u}{2}\sum_i n_i (n_i-1)
$$

# Arguments

  * `address`: the starting address, defines number of particles and sites.
  * `u`: the interaction parameter.
  * `t`: the hopping strength.

# See also

  * [`HubbardMom1D`](@ref)
  * [`ExtendedHubbardReal1D`](@ref)
