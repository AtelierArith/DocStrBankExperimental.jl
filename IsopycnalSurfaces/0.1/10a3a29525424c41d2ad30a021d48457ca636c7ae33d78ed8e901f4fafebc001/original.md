```
function vars2sigma1(vars,p,σgrid;spline_order,linearinterp,eos)
map variables from regular 3D grid onto σ₀ surfaces
```

# Arguments

  * `vars::Dict{String,Array{T,3}}}`: dict of 3d arrays
  * `p::Vector{T}`: vertical profile of standard pressures
  * `σgrid`: σ surface values
  * `splorder`: 1-5, order of spline, optional keyword argument, default=3
  * `linearinterp`: optional keyword logical argument, default=false
  * `eos`: optional keyword string for equation of state, default = "EOS80"

# Output

  * `varsσ::Dict{String,Array{T,3}`: dict of 3d arrays of variables on sigma1 surfaces
