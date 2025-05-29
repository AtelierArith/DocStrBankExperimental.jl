```
download_osm_network(download_method::Symbol;
                     network_type::Symbol=:drive,
                     metadata::Bool=false,
                     download_format::Symbol=:json,
                     save_to_file_location::Union{String,Nothing}=nothing,
                     download_kwargs...
                     )::Union{XMLDocument,Dict{String,Any}}
```

Downloads an OpenStreetMap network by querying with a place name, bounding box, or centroid point.

# Arguments

  * `download_method::Symbol`: Download method, choose from `:place_name`, `:bbox` or `:point`.
  * `network_type::Symbol=:drive`: Network type filter, pick from `:drive`, `:drive_service`, `:walk`, `:bike`, `:all`, `:all_private`, `:none`, `:rail`
  * `metadata::Bool=false`: Set true to return metadata.
  * `download_format::Symbol=:json`: Download format, either `:osm`, `:xml` or `json`.
  * `save_to_file_location::Union{String,Nothing}=nothing`: Specify a file location to save downloaded data to disk.

# Required Kwargs for each Download Method

*`download_method=:place_name`*

  * `place_name::String`: Any place name string used as a search argument to the Nominatim API.

*`download_method=:bbox`*

  * `minlat::AbstractFloat`: Bottom left bounding box latitude coordinate.
  * `minlon::AbstractFloat`: Bottom left bounding box longitude coordinate.
  * `maxlat::AbstractFloat`: Top right bounding box latitude coordinate.
  * `maxlon::AbstractFloat`: Top right bounding box longitude coordinate.

*`download_method=:point`*

  * `point::GeoLocation`: Centroid point to draw the bounding box around.
  * `radius::Number`: Distance (km) from centroid point to each bounding box corner.

*`download_method=:polygon`*

  * `polygon::AbstractVector`: Vector of longitude-latitude pairs.

*`download_method=:custom_filters`*

  * `custom_filters::String`: Filters for the query, e.g. polygon filter, highways only, traffic lights only, etc.
  * `metadata::Bool=false`: Set true to return metadata.
  * `download_format::Symbol=:json`: Download format, either `:osm`, `:xml` or `json`.
  * `bbox::Union{Vector{AbstractFloat},Nothing}=nothing`: Optional bounding box filter.

# Network Types

  * `:drive`: Motorways excluding private and service ways.
  * `:drive_service`: Motorways including private and service ways.
  * `:walk`: Walkways only.
  * `:bike`: Cycleways only.
  * `:all`: All motorways, walkways and cycleways excluding private ways.
  * `:all_private`: All motorways, walkways and cycleways including private ways.
  * `:none`: No network filters.
  * `:rail`: Railways excluding proposed and platform.

# Return

  * `Union{XMLDocument,Dict{String,Any}}`: OpenStreetMap network data parsed as either XML or Dictionary object depending on the download method.
