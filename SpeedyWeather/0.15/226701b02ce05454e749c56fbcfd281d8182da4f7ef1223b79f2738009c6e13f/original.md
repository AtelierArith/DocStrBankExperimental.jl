Intermediate quantities for the dynamics of a given layer.

  * `trunc::Int64`
  * `nlat_half::Int64`
  * `nlayers::Int64`
  * `a::Any`: Multi-purpose a, 3D work array to be reused in various places
  * `b::Any`: Multi-purpose b, 3D work array to be reused in various places
  * `a_grid::Any`: Multi-purpose a, 3D work array to be reused in various places
  * `b_grid::Any`: Multi-purpose b, 3D work array to be reused in various places
  * `a_2D::Any`: Multi-purpose a, work array to be reused in various places
  * `b_2D::Any`: Multi-purpose b, work array to be reused in various places
  * `a_2D_grid::Any`: Multi-purpose a, work array to be reused in various places
  * `b_2D_grid::Any`: Multi-purpose b, work array to be reused in various places
  * `uv∇lnp::Any`: Pressure flux (uₖ, vₖ)⋅∇ln(pₛ)
  * `uv∇lnp_sum_above::Any`: Sum of Δσₖ-weighted uv∇lnp above
  * `div_sum_above::Any`: Sum of div_weighted from top to k
  * `temp_virt::Any`: Virtual temperature [K], spectral for geopotential
  * `geopot::Any`: Geopotential [m²/s²] on full layers
  * `σ_tend::Any`: Vertical velocity (dσ/dt), on half levels k+1/2 below, pointing to the surface (σ=1)
  * `∇lnp_x::Any`: Zonal gradient of log surf pressure
  * `∇lnp_y::Any`: Meridional gradient of log surf pressure
  * `u_mean_grid::Any`: Vertical average of zonal velocity [m/s]
  * `v_mean_grid::Any`: Vertical average of meridional velocity [m/s]
  * `div_mean_grid::Any`: Vertical average of divergence [1/s], grid
  * `div_mean::Any`: Vertical average of divergence [1/s], spectral
