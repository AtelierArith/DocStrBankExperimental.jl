```
metadata!(df::AbstractDataFrame, key::AbstractString, value; style::Symbol=:default)
metadata!(dfr::DataFrameRow, key::AbstractString, value; style::Symbol=:default)
metadata!(dfc::DataFrameColumns, key::AbstractString, value; style::Symbol=:default)
metadata!(dfr::DataFrameRows, key::AbstractString, value; style::Symbol=:default)
```

Set table-level metadata for object `df` for key `key` to have value `value` and style `style` (`:default` by default) and return `df`.

For `SubDataFrame` and `DataFrameRow` only `:note`-style is allowed. Trying to set a key-value pair for which the key already exists in the parent data frame with another style throws an error.

See also: [`metadata`](@ref), [`metadatakeys`](@ref), [`deletemetadata!`](@ref), [`emptymetadata!`](@ref), [`colmetadata`](@ref), [`colmetadatakeys`](@ref), [`colmetadata!`](@ref), [`deletecolmetadata!`](@ref), [`emptycolmetadata!`](@ref).

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
