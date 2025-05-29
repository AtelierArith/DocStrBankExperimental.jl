```
ExtendedHubbardReal1D(address; u=1.0, v=1.0, t=1.0, boundary_condition=:periodic)
```

Implements the extended Hubbard model on a one-dimensional chain in real space. This Hamiltonian can be either real or complex, depending on the choice of `boundary_condition`.

$$
\hat{H} = -t \sum_{\langle i,j\rangle} a_i^† a_j + \frac{u}{2}\sum_i n_i (n_i-1) +
v \sum_{\langle i,j\rangle} n_i n_j
$$

# Arguments

  * `address`: the starting address.
  * `u`: on-site interaction parameter
  * `v`: the next-neighbor interaction
  * `t`: the hopping strength
  * `boundary_condition` The following values are supported:

      * `:periodic`: usual period boundary condition realising a ring geometry.
      * `:hard_wall`: hopping over the boundary is not allowed.
      * `:twisted`: like `:periodic` but hopping over the boundary incurs an additional factor of `-1`.
      * `θ <: Number`: like `:periodic` and `:twisted` but hopping over the boundary incurs a factor $\exp(iθ)$ for a hop to the right and $\exp(−iθ)$ for a hop to the left. With this choice the Hamiltonian will have a complex `eltype` whereas otherwise the `eltype` is determined by the type of the parameters `t`, `u`, and `v`.

See also [`HubbardRealSpace`](@ref).
