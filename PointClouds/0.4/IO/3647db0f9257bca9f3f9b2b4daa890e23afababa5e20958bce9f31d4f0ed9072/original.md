```
PointRecord{F,N}
```

A point data record in the point data record format (PDRF) `F` (usually between 0 and 10) with `N` extra bytes (usually zero), as defined in the ASPRS “LAS” format.

## Point record attributes

The attributes of point records can be accessed with the functions below; directly accessing struct fields is discouraged. Note that some attributes are not all available for all PDRFs.

  * 3D position: [`coordinates`](@ref)
  * color information: [`color_channels`](@ref) *(RGB for PDRFs 2/3/5/7, RGB + NIR for PDRFs 8/10)*
  * information about the laser pulse return: [`intensity`](@ref), [`return_number`](@ref), [`return_count`](@ref), [`waveform_packet`](@ref) *(PDRFs 4/5/9/10 only)*
  * point record classification: [`classification`](@ref), [`is_key_point`](@ref), [`is_overlap`](@ref) *(all PDRFs, based on classification for PDRF 0–5)*, [`is_synthetic`](@ref), [`is_withheld`](@ref)
  * scanner/flight path information: [`scan_angle`](@ref) *(higher resolution for PDRFs 6–10)*, [`is_left_to_right`](@ref), [`is_right_to_left`](@ref), [`is_edge_of_line`](@ref), [`scanner_channel`](@ref) *(PDRFs 6–10 only)*, [`source_id`](@ref), [`gps_time`](@ref) *(PDRFs 1 & 3–10)*
  * custom attributes: [`user_data`](@ref), [`extra_bytes`](@ref)

These functions all have a similar signature:

```
attribute([T], p::PointRecord)
attribute([T], points, inds = :)
```

The attribute can be read from a single point record `p` or from the collection `points` at one or multiple indices `inds` (`:` by default), returning a vector of attribute values in the latter case. By default, the values are returned as normalized `Float64` or `Int` values such that the caller does not have to be aware of the details of how the data is stored in different PDRFs. The optional type argument `T` can be used to specify an integer type that the raw values are converted to (without normalization), or simply set to `Integer` to obtain the raw values.
