```
metadata(df::AbstractDataFrame, key::AbstractString, [default]; style::Bool=false)
metadata(dfr::DataFrameRow, key::AbstractString, [default]; style::Bool=false)
metadata(dfc::DataFrameColumns, key::AbstractString, [default]; style::Bool=false)
metadata(dfr::DataFrameRows, key::AbstractString, [default]; style::Bool=false)
```

Return table-level metadata value associated with `df` for key `key`. If `style=true` return a tuple of metadata value and metadata style.

`SubDataFrame` and `DataFrameRow` expose only `:note`-style metadata of their parent.

If `default` is passed then return it if `key` does not exist; if `style=true` return `(default, :default)`.

See also: [`metadatakeys`](@ref), [`metadata!`](@ref), [`deletemetadata!`](@ref), [`emptymetadata!`](@ref), [`colmetadata`](@ref), [`colmetadatakeys`](@ref), [`colmetadata!`](@ref), [`deletecolmetadata!`](@ref), [`emptycolmetadata!`](@ref).

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
