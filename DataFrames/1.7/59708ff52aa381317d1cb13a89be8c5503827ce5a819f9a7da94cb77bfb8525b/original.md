```
metadatakeys(df::AbstractDataFrame)
metadatakeys(dfr::DataFrameRow)
metadatakeys(dfc::DataFrameColumns)
metadatakeys(dfr::DataFrameRows)
```

Return an iterator of table-level metadata keys which are set in the object.

Values can be accessed using [`metadata(df, key)`](@ref).

`SubDataFrame` and `DataFrameRow` expose only `:note`-style metadata keys of their parent.

See also: [`metadata`](@ref), [`metadata!`](@ref), [`deletemetadata!`](@ref), [`emptymetadata!`](@ref), [`colmetadata`](@ref), [`colmetadatakeys`](@ref), [`colmetadata!`](@ref), [`deletecolmetadata!`](@ref), [`emptycolmetadata!`](@ref).

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
