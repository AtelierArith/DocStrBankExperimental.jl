```
create_dataset(parent, path, datatype, dataspace; properties...)
```

# Arguments

  * `parent` - `File` or `Group`
  * `path` - `String` describing the path of the dataset within the HDF5 file or          `nothing` to create an anonymous dataset
  * `datatype` - `Datatype` or `Type` or the dataset
  * `dataspace` - `Dataspace` or `Dims` of the dataset
  * `properties` - keyword name-value pairs set properties of the dataset

# Keywords

There are many keyword properties that can be set. Below are a few select keywords.

  * `chunk` - `Dims` describing the size of a chunk. Needed to apply filters.
  * `filters` - `AbstractVector{<: Filters.Filter}` describing the order of the filters to apply to the data. See [`Filters`](@ref)
  * `external` - `Tuple{AbstractString, Intger, Integer}` `(filepath, offset, filesize)` External dataset file location, data offset, and file size. See [`API.h5p_set_external`](@ref).

Additionally, the initial create, transfer, and access properties can be provided as a keyword:

  * `dcpl` - [`DatasetCreateProperties`](@ref)
  * `dxpl` - [`DatasetTransferProperties`](@ref)
  * `dapl` - [`DatasetAccessProperties`](@ref)
