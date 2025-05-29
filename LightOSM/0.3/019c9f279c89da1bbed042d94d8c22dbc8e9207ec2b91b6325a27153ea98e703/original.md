```
buildings_from_download(download_method::Symbol;
                        metadata::Bool=false,
                        download_format::Symbol=:osm,
                        save_to_file_location::Union{String,Nothing}=nothing,
                        download_kwargs...
                        )::Dict{Integer,Building}
```

Downloads and Creates `Building` objects from OpenStreetMap APIs.

# Arguments

  * `download_method::Symbol`: Download method, choose from `:place_name`, `:bbox` or `:point`.
  * `metadata::Bool=false`: Set true to return metadata.
  * `download_format::Symbol=:osm`: Download format, either `:osm`, `:xml` or `json`.
  * `save_to_file_location::Union{String,Nothing}=nothing`: Specify a file location to save downloaded data to disk.

# Required Download Kwargs

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

# Return

  * `Dict{Integer,Building}`: Mapping from building relation/way ids to `Building` objects.
