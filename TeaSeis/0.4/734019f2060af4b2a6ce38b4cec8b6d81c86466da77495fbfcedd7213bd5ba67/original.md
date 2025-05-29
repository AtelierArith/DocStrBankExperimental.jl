```
jsopen(filename, mode, [parameters])
```

Open a new or existing JavaSeis dataset with name `filename::String` and in `mode::String`. `mode` can be one of `"r"` (read), `"w"` (write/create) or `"r+"` (read and write). It is convention for filename to havea ".js" extention.

If `"w"` is used for the value of `mode`, then the `axis_lengths` named parameter is required, and several optional named function parameters are available:

# parameters

  * `similarto::String` An existing JavaSeis dataset.  If set, then all other named arguments can be used to modify the data context that belongs to the existing JavaSeis dataset.
  * `description::String` Description of dataset, if not set, then a description is parsed from the filename.
  * `mapped::Bool` If the dataset is full (no missing frames/traces), then it may be more efficient to set this to `false`.  Defaults to `true`.
  * `datatype::String` Examples are `CMP`, `SHOT`, etc.  If not set, then `UNKNOWN` is used.
  * `dataformat::Type` Choose from `Float32`, and `Int16`.  If not set, then `Float32` is used.
  * `dataorder::String` (not supported)
  * `axis_lengths::Array{Int}` size of each dimension (sample/trace/frame/volume/hypercube) of the JavaSeis data context
  * `axis_propdefs::Array{TracePropertyDef}` Trace properties corresponding to JavaSeis axes.  If not set, then `SAMPLE`, `TRACE`, `FRAME`, `VOLUME` and `HYPRCUBE` are used.
  * `axis_units::Array{String}` Units corresponding to JavaSeis axes. e.g. `SECONDS`, `METERS`, etc.  If not set, then `UNKNOWN` is used.
  * `axis_domains::Array{String}` Domains corresponding to JavaSeis axes. e.g. `SPACE`, `TIME`, etc.  If not set, then `UNKNOWN` is used.
  * `axis_lstarts::Array{Int}` Logical origins for each axis.  If not set, then `1` is used for the logical origin of each axis.
  * `axis_lincs::Array{Int}` Logical increments for each axis.  If not set, then `1` is used for the logical increments of each axis.
  * `axis_pstarts::Array{Float64}` Physical origins for each axis.  If not set, then `0.0` is used for the physical origin of each axis.
  * `axis_pincs::Array{Float64}` Physical increments for each axis.  If not set, then `1.0` is used for the physical increments of each axis.
  * `data_properties::Array{DataProperty}` An array of custom trace properties.  These are in addition to the properties listed in `SSPROPS.md`.
  * `properties::Array{TracePropertyDef}` An array of custom data properties.  One property per data-set rather than one property per trace as in `properties` above.
  * `geometry::Geometry` An optional three point geometry can be embedded in the JavaSeis file.
  * `secondaries::Array{String}` An array of file-system locations used to store the file extents.  If not set, then *primary* storage is used.
  * `nextents::Int64` The number of file-extents used to store the data.  If not set, then a heuristic is used to choose the number of extents.  The heuristic is: min(256,10 + (FRAMEWORK_SIZE)/(2*1024^3)).
  * `properties_add::Array{TracePropertyDef}` When `similarto` is specified, use this to add trace properties to those already existing in the `similarto` file.
  * `properties_rm::Array{TracePropertyDef}` When `similarto` is specified, use this to remove trace properties to those already existing in the `similarto` file.
  * `dataproperties_add::Array{DataProperty}` When `similarto` is specfied, use this to add dataset properties to those aloready existing in the `similarto` file.
  * `dataproperties_rm::Array{DataProperty}` When `similarto` is specified, use this to remove dataset properties to those already existing in the `similarto` file.
