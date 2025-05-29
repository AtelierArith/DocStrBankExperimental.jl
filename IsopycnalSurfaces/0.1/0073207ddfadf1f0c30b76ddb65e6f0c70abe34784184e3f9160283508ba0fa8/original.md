```
function sigmacolumn(θ,S,p,p0,eos="EOS80")
σ for a water column
```

# Arguments

  * `θz::Vector{T}`: potential temperature
  * `Sz::Vector{T}`: practical salinity
  * `pz::Vector{T}`: vertical profile of standard pressures
  * `p₀`: reference pressure
  * `eos:String`: optional argument for equation of state, default = "EOS80"

# Output

  * `σ::Vector{T}`:  sigma for wet points in column
