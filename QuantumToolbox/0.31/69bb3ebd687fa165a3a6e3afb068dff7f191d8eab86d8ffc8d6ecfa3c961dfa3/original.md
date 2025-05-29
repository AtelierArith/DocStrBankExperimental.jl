```
DissipativeIsing(Jx::Real, Jy::Real, Jz::Real, hx::Real, hy::Real, hz::Real, γ::Real, latt::Lattice; boundary_condition::Union{Symbol, Val} = Val(:periodic_bc), order::Integer = 1)
```

A Julia constructor for a dissipative Ising model. The function returns the Hamiltonian

$$
\hat{H} = \frac{J_x}{2} \sum_{\langle i, j \rangle} \hat{\sigma}_i^x \hat{\sigma}_j^x + \frac{J_y}{2} \sum_{\langle i, j \rangle} \hat{\sigma}_i^y \hat{\sigma}_j^y + \frac{J_z}{2} \sum_{\langle i, j \rangle} \hat{\sigma}_i^z \hat{\sigma}_j^z + h_x \sum_i \hat{\sigma}_i^x
$$

and the collapse operators

$$
\hat{c}_i = \sqrt{\gamma} \hat{\sigma}_i^-
$$

# Arguments

  * `Jx::Real`: The coupling constant in the x-direction.
  * `Jy::Real`: The coupling constant in the y-direction.
  * `Jz::Real`: The coupling constant in the z-direction.
  * `hx::Real`: The magnetic field in the x-direction.
  * `hy::Real`: The magnetic field in the y-direction.
  * `hz::Real`: The magnetic field in the z-direction.
  * `γ::Real`: The local dissipation rate.
  * `latt::Lattice`: A [`Lattice`](@ref) object that defines the geometry of the lattice.
  * `boundary_condition::Union{Symbol, Val}`: The boundary conditions of the lattice. The possible inputs are `periodic_bc` and `open_bc`, for periodic or open boundary conditions, respectively. The default value is `Val(:periodic_bc)`.
  * `order::Integer`: The order of the nearest-neighbour sites. The default value is 1.
