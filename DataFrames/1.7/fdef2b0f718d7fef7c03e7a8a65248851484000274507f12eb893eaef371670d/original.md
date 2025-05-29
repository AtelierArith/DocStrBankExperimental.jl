```
deletemetadata!(df::AbstractDataFrame, key::AbstractString)
deletemetadata!(dfr::DataFrameRow, key::AbstractString)
deletemetadata!(dfc::DataFrameColumns, key::AbstractString)
deletemetadata!(dfr::DataFrameRows, key::AbstractString)
```

Delete table-level metadata from object `df` for key `key` and return `df`. If key does not exist, return `df` without modification.

For `SubDataFrame` and `DataFrameRow` only `:note`-style metadata from their parent can be deleted (as other styles are not propagated to views).

See also: [`metadata`](@ref), [`metadatakeys`](@ref), [`metadata!`](@ref), [`emptymetadata!`](@ref), [`colmetadata`](@ref), [`colmetadatakeys`](@ref), [`colmetadata!`](@ref), [`deletecolmetadata!`](@ref), [`emptycolmetadata!`](@ref).

# Examples

```jldoctest
julia> df = DataFrame(a=1, b=2);

julia> metadatakeys(df)
()

julia> metadata!(df, "name", "example", style=:note);

julia> metadatakeys(df)
KeySet for a Dict{String, Tuple{Any, Any}} with 1 entry. Keys:
  "name"

julia> metadata(df, "name")
"example"

julia> metadata(df, "name", style=true)
("example", :note)

julia> deletemetadata!(df, "name");

julia> metadatakeys(df)
()
```

```
