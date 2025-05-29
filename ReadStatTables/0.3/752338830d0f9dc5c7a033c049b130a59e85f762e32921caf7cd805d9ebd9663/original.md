```
ReadStatTable(table, ext::AbstractString; kwargs...)
```

Construct a `ReadStatTable` by wrapping a `Tables.jl`-compatible column table for a supported file format with extension `ext`. An attempt is made to collect table-level or column-level metadata with a key that matches a metadata field in [`ReadStatMeta`](@ref) or [`ReadStatColMeta`](@ref) via the `metadata` and `colmetadata` interface defined by `DataAPI.jl`.

This method is used by [`writestat`](@ref) when the provided `table` is not already a `ReadStatTable`. Hence, it is useful for gaining fine-grained control over the content to be written. Metadata may be manually specified with keyword arguments.

Any `missing` existing in string columns will be replaced by an empty string `""`. A column with element type `Missing` is treated as a column with empty strings.

# Keywords

  * `copycols::Bool = true`: copy data columns to `ReadStatColumns`; this is required for writing columns of date/time values (that are not already represented by numeric values).
  * `refpoolaslabel::Bool = true`: generate value labels for columns of an array type that makes use of `DataAPI.refpool` (e.g., `CategoricalArray` and `PooledArray`).
  * `vallabels::Dict{Symbol, Dict} = Dict{Symbol, Dict}()`: a dictionary of all value label dictionaries indexed by their names.
  * `hasmissing::Vector{Bool} = Vector{Bool}()`: a vector of indicators for whether any missing value present in the corresponding column; irrelavent for writing tables.
  * `meta::ReadStatMeta = ReadStatMeta()`: file-level metadata.
  * `colmeta::ColMetaVec = ReadStatColMetaVec()`: variable-level metadata stored in a `StructArray` of `ReadStatColMeta`s; values are always overwritten.
  * `varformat::Union{Dict{Symbol,String}, Nothing} = nothing`: specify variable-level format for certain variables with the key being the variable name (as `Symbol`) and value being the format string.
  * `styles::Dict{Symbol, Symbol} = _default_metastyles()`: metadata styles.
  * `maxdispwidth::Integer = 60`: maximum `display_width` set for any variable.
