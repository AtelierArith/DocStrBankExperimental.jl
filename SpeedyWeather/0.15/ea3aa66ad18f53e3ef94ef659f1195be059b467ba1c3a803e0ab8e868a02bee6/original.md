Construct Geometry struct containing parameters and arrays describing an iso-latitude grid `<:AbstractGrid` and the vertical levels. Pass on `SpectralGrid` to calculate the following fields

  * `spectral_grid::SpeedyWeather.SpectralGrid`: SpectralGrid that defines spectral and grid resolution
  * `nlat_half::Int64`: resolution parameter nlat_half of Grid, # of latitudes on one hemisphere (incl Equator)
  * `nlon_max::Int64`: maximum number of longitudes (at/around Equator)
  * `nlat::Int64`: number of latitude rings
  * `nlayers::Int64`: number of vertical levels
  * `npoints::Int64`: total number of horizontal grid points
  * `radius::Any`: Planet's radius [m]
  * `lond::Any`: array of longitudes in degrees (0...360˚), empty for non-full grids
  * `latd::Any`: array of latitudes in degrees (90˚...-90˚)
  * `lat::Any`: array of latitudes in radians (π...-π)
  * `colat::Any`: array of colatitudes in radians (0...π)
  * `londs::Any`: longitude (0˚...360˚) for each grid point in ring order
  * `latds::Any`: latitude (-90˚...˚90) for each grid point in ring order
  * `lons::Any`: longitude (0...2π) for each grid point in ring order
  * `lats::Any`: latitude (-π/2...π/2) for each grid point in ring order
  * `sinlat::Any`: sin of latitudes
  * `coslat::Any`: cos of latitudes
  * `coslat⁻¹::Any`: = 1/cos(lat)
  * `coslat²::Any`: = cos²(lat)
  * `coslat⁻²::Any`: # = 1/cos²(lat)
  * `σ_levels_half::Any`: σ at half levels, σ_k+1/2
  * `σ_levels_full::Any`: σ at full levels, σₖ
  * `σ_levels_thick::Any`: σ level thicknesses, σₖ₊₁ - σₖ
  * `ln_σ_levels_full::Any`: log of σ at full levels, include surface (σ=1) as last element
  * `full_to_half_interpolation::Any`: Full to half levels interpolation
