```
mutable struct GMTimage{T<:Union{Unsigned, Bool}, N} <: AbstractArray{T,N}
```

The GMTimage type is how images (UInt8, UInt16), 2D or multi-layered, (geo)referenced or not, communicate in/out with the GMT and GDAL libraries. They implement the AbstractArray interface.

The fields of this struct are:

  * `proj4::String`:              Projection string in PROJ4 syntax (Optional)
  * `wkt::String`:                Projection string in WKT syntax (Optional)
  * `epsg::Int`:                  EPSG code
  * `geog::Int`:                  Is geographic coords? 0 -> No; 1 -> [-180 180]; 2 -> [0 360]
  * `range::Vector{Float64}`:     1x6[8] vector with [x*min, x*max, y*min, y*max, z*min, z*max [, v*min, v*max]]
  * `inc::Vector{Float64}`:       1x2[3] vector with [x*inc, y*inc [,v_inc]]
  * `registration::Int`:          Registration type: 0 -> Grid registration; 1 -> Pixel registration
  * `nodata::Float32`:            The value of nodata
  * `color_interp::String`:       If equal to "Gray" an indexed image with no cmap will get a gray cmap
  * `metadata::Vector{String}`:   To store any metadata that can eventually be passed to GDAL (Optional)
  * `names::Vector{String}`:      To use whith multi-band and when bands have names (Optional)
  * `x::Vector{Float64}`:         [1 x n_columns] vector with XX coordinates
  * `y::Vector{Float64}`:         [1 x n_rows]    vector with YY coordinates
  * `v::Vector{Float64}`:         [v x n_bands]   vector with vertical coords or wavelengths in hypercubes (Optional)
  * `image::Array{T,N}`:          [n*rows x n*columns x n_bands] image array
  * `labels::Vector{String}`:     Labels of a Categorical CPT
  * `n_colors::Int`:              Number of colors stored in the vector 'colormap'
  * `colormap::Vector{Int32}`:    A vector with n_colors-by-4 saved column-wise
  * `alpha::Matrix{UInt8}`:       A [n*rows x n*columns] alpha array
  * `layout::String`:             A four character string describing the image memory layout
  * `pad::Int`:                   When != 0 means that the array is placed in a padded array of PAD rows/cols
