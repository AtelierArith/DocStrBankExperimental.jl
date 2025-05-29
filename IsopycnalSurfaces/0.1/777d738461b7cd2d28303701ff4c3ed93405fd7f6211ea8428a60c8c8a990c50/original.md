```
function var2sigmacolumn(σ,v,σgrid;splorder,linearinterp)
map θ,S, p onto σ₁ surfaces for a water column
```

# Arguments

  * `σ`::Array{Float,1}}`: sigma values of input variable
  * `v::Array{Float,1}}`: variable of interest
  * `σgrid`: σ surface values
  * `splorder`: optional argument of 1-5, order of spline, default=3
  * `linearinterp`: optional argument, true to force linear interpolation, default=false

# Output

  * `θonσ`: variable on sigma surfaces
