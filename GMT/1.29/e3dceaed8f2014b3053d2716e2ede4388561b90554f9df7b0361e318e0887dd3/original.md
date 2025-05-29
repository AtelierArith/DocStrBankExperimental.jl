```
mutable struct GMTdataset{T<:Real, N} <: AbstractArray{T,N}
```

The GMTdataset type is how tables, (geo)referenced or not, communicate in/out with the GMT and GDAL libraries. They implement the AbstractArray and Tables interface.

The fields of this struct are:

  * `data::Array{T,N}`:             Mx2 Matrix with segment data
  * `ds_bbox::Vector{Float64}`:     Global BoundingBox (for when there are many segments)
  * `bbox::Vector{Float64}`:        Segment BoundingBox
  * `attrib::Dict{String, Union{String, Vector{String}}}`: Dictionary with attributes/values (optional)
  * `colnames::Vector{String}`:     Column names. Antecipate using this with a future Tables inerface
  * `text::Vector{String}`:         Array with text after data coordinates (mandatory only when plotting Text)
  * `header::String`:               String with segment header (Optional but sometimes very useful)
  * `comment::Vector{String}`:      Array with any dataset comments [empty after first segment]
  * `proj4::String`:                Projection string in PROJ4 syntax (Optional)
  * `wkt::String`:                  Projection string in WKT syntax (Optional)
  * `epsg::Int`:                    EPSG projection code (Optional)
  * `geom::Integer`:                Geometry type. One of the GDAL's enum (wkbPoint, wkbPolygon, etc...)
