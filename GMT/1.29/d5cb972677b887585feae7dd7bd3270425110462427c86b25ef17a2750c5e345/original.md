```
mutable struct GMTcpt
```

The fields of this struct are:

  * `colormap::Array{Float64,2}`:  Mx3 matrix equal to the first three columns of cpt
  * `alpha::Array{Float64,1}`:     Vector of alpha values. One for each color.
  * `range::Array{Float64,2}`:     Mx2 matrix with z range for each slice
  * `minmax::Array{Float64,1}`:    Two elements Vector with zmin,zmax
  * `bfn::Array{Float64,2}`:       A 3x3(4?) matrix with BFN colors (one per row) in [0 1] interval
  * `depth::Cint`:                 Color depth: 24, 8, 1
  * `hinge::Cdouble`:              Z-value at discontinuous color break, or NaN
  * `cpt::Array{Float64,2}`:       Mx6 matrix with r1 g1 b1 r2 g2 b2 for z1 z2 of each slice
  * `egorical::Int`:               Is this CPT categorical? 0 = No, 1 = Yes, 2 = Yes and keys are strings.
  * `label::Vector{String}`:       Labels of a Categorical CPT
  * `key::Vector{String}`:         Keys of a Categorical CPT
  * `model::String`:               String with color model rgb, hsv, or cmyk [rgb]
  * `comment::Vector{String}`:     Cell array with any comments
