```
ReadStatMeta <: AbstractMetaDict
```

A collection of file-level metadata associated with a data file processed with `ReadStat`.

Metadata can be retrieved and modified from the associated [`ReadStatTable`](@ref) via methods compatible with `DataAPI.jl`. A dictionary-like interface is also available for directly working with `ReadStatMeta`.

# Fields

  * `row_count::Int`: number of rows returned by `ReadStat` parser; being `-1` if not available in metadata; may reflect the value set with the `row_limit` parser option instead of the actual number of rows in the data file.
  * `var_count::Int`: number of data columns returned by `ReadStat` parser.
  * `creation_time::DateTime`: timestamp for file creation.
  * `modified_time::DateTime`: timestamp for file modification.
  * `file_format_version::Int`: version number of file format.
  * `file_format_is_64bit::Bool`: indicator for 64-bit file format; only relevant to SAS.
  * `compression::readstat_compress_t`: file compression mode; only relevant to certain file formats.
  * `endianness::readstat_endian_t`: endianness of data file.
  * `table_name::String`: name of the data table; only relevant to `.xpt` format.
  * `file_label::String`: label of data file.
  * `file_encoding::String`: character encoding of data file.
  * `notes::Vector{String}`: notes attached to data file.
  * `file_ext::String`: file extension of data file.
