```
mutable struct GMTgrid{T<:Number,N} <: AbstractArray{T,N}
```

The GMTgrid type is how grids, 2D or multi-layered, (geo)referenced or not, communicate in/out with the GMT and GDAL libraries. They implement the AbstractArray interface.

The fields of this struct are:

  * `proj4::String`:                      Projection string in PROJ4 syntax (Optional)
  * `wkt::String`:                        Projection string in WKT syntax (Optional)
  * `epsg::Int`:                          EPSG code
  * `geog::Int`:                          Is geographic coords? 0 -> No; 1 -> [-180 180]; 2 -> [0 360]
  * `range::Vector{Float64}`:             1x6[8] vector with [x*min, x*max, y*min, y*max, z*min, z*max [, v*min, v*max]]
  * `inc::Vector{Float64}`:               1x2[3] vector with [x*inc, y*inc [,v_inc]]
  * `registration::Int`:                  Registration type: 0 -> Grid registration; 1 -> Pixel registration
  * `nodata::Union{Float64, Float32}`:    The value of nodata
  * `title::String`:                      Title (Optional)
  * `comment::String`:                    Remark (Optional)
  * `command::String`:                    Command used to create the grid (Optional)
  * `cpt::String`:                        Name of a recommended GMT CPT name for this grid.
  * `names::Vector{String}`:              To use whith multi-layered and when layers have names (Optional)
  * `x::Vector{Float64}`:                 [1 x n_columns] vector with XX coordinates
  * `y::Vector{Float64}`:                 [1 x n_rows]    vector with YY coordinates
  * `v::Union{Vector{<:Real}, Vector{String}}`:    [v x n_bands]   vector with VV (vertical for 3D grids) coordinates
  * `z::Array{T,N}`:                      [n*rows x n*columns] grid array
  * `x_unit::String`:                     Units of XX axis (Optional)
  * `y_unit::String`:                     Units of YY axis (Optional)
  * `v_unit::String`:                     Units of Vertical axis (Optional)
  * `z_unit::String`:                     Units of z vlues (Optional)
  * `layout::String`:                     A three character string describing the grid memory layout
  * `scale::Union{Float64, Float32}=1f0`: When saving in file apply `z = z * scale + offset`
  * `offset::Union{Float64, Float32}=0f0`
  * `pad::Int=0`:                         When != 0 means that the array is placed in a padded array of PAD rows/cols
  * `hasnans::Int=0`:                     0 -> "don't know"; 1 -> confirmed, "have no NaNs"; 2 -> confirmed, "have NaNs"
