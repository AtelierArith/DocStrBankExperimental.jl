`LAS` represents point-cloud data in the ASPRS “LAS” format, consisting of a collection of [`PointRecord`](@ref)s as well as a number of global attributes describing the point-cloud data. Use [`Base.show`](https://docs.julialang.org/en/v1/base/io-network/#Base.show-Tuple%7BIO,%20Any%7D) to get a summary of the data, use indexing to access point records, use property access (e.g. `las.project_id`) to read global attributes, and use [`update`](@ref update(::LAS, ::NamedTuple)) to change global and per-point attributes.

# Point data records

The [`PointRecord`](@ref)s of a `LAS` can be accessed through indexing. Note that when loading `LAS` data from a file (e.g. with [`LAS(filename)`](@ref PointClouds.IO.LAS(::IO))), the point records are not loaded into memory by default. Instead, the data is loaded in a lazy manner once it is accessed, which allows working with files that do not fit into memory. The `points` field of `LAS` gives access to the internal representation of the point records but direct use is discouraged.

Point records are usually stored in one of 11 standardized point data record formats (PDRFs) ranging from `PointRecord{0}` to `PointRecord{10}`. While all PDRFs have many attributes (such as 3D coordinates and return intensity) in common, the PDRFs differ in the exact set of attributes they support and the precision at which the data is stored. As of LAS version 1.4, the PDRFs 0–5 are considered legacy formats and the newer PDRFs 6–10 are preferred.

Refer to the [`PointRecord`](@ref) help text for the list of functions that can be called on them to access their attributes. These accessor functions can also be called directly on the `LAS` with one or multiple indices to access point attributes.

# Variable length records (VLRs)

The variable length records of a LAS file store information about the coordinate reference system (CRS), which can be accessed with the [`getcrs`](@ref) function. The raw VLR data can be accessed through the `vlr` field of `LAS`.

# Global point cloud attributes

  * `coord_scale::NTuple{3,Float64}`
  * `coord_offset::NTuple{3,Float64}`
  * `coord_min::NTuple{3,Float64}`
  * `coord_max::NTuple{3,Float64}`
  * `return_counts::Vector{UInt64}`
  * `version::Tuple{UInt8,UInt8}`: The version of the LAS file format (1.0 to 1.4) in the form of a `(major, minor)` tuple.
  * `source_id::UInt16`
  * `project_id::GUID`
  * `system_id::String`
  * `software_id::String`
  * `creation_date::Tuple{UInt16,UInt16}`
  * `has_adjusted_standard_gps_time::Bool`
  * `has_internal_waveform::Bool`
  * `has_external_waveform::Bool`
  * `has_synthetic_return_numbers::Bool`
  * `has_well_known_text::Bool`
