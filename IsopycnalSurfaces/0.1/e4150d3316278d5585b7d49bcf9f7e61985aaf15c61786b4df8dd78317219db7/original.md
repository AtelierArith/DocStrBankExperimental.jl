```
function sigma0column(θ,S,p)
σ₀ for a water column
Untested for a mix of float values
```

# Arguments

  * `θz::Vector{T}`: potential temperature
  * `Sz::Vector{T}`: practical salinity
  * `pz::Vector{T}`: vertical profile of standard pressures

# Output

  * `σ₀`:  sigma-0 for wet points in column
