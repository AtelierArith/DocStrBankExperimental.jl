```
names(df::AbstractDataFrame, cols=:)
names(df::DataFrameRow, cols=:)
names(df::GroupedDataFrame, cols=:)
names(df::DataFrameRows, cols=:)
names(df::DataFrameColumns, cols=:)
names(df::GroupKey)
```

Return a freshly allocated `Vector{String}` of names of columns contained in `df`.

If `cols` is passed then restrict returned column names to those matching the selector (this is useful in particular with regular expressions, `Cols`, `Not`, and `Between`). `cols` can be:

  * any column selector (`Symbol`, string or integer; `:`, `Cols`, `All`, `Between`, `Not`, a regular expression, or a vector of `Symbol`s, strings or integers); these column selectors are documented in the [General rules](@ref) section of the [Indexing](@ref) part of the DataFrames.jl manual
  * a `Type`, in which case names of columns whose `eltype` is a subtype of `T` are returned
  * a `Function` predicate taking the column name as a string and returning `true` for columns that should be kept

See also [`propertynames`](@ref) which returns a `Vector{Symbol}` (except for `GroupedDataFrame` in which case use `Symbol.(names(df))`).

# Examples

```jldoctest
julia> df = DataFrame(x1=[1, missing, missing], x2=[3, 2, 4], x3=[3, missing, 2], x4=Union{Int, Missing}[2, 4, 4])
3×4 DataFrame
 Row │ x1       x2     x3       x4
     │ Int64?   Int64  Int64?   Int64?
─────┼─────────────────────────────────
   1 │       1      3        3       2
   2 │ missing      2  missing       4
   3 │ missing      4        2       4

julia> names(df)
4-element Vector{String}:
 "x1"
 "x2"
 "x3"
 "x4"

julia> names(df, Int) # pick columns whose element type is Int
1-element Vector{String}:
 "x2"

julia> names(df, x -> x[end] == '2') # pick columns for which last character in their name is '2'
1-element Vector{String}:
 "x2"

julia> fun(col) = sum(skipmissing(col)) >= 10
fun (generic function with 1 method)

julia> names(df, fun.(eachcol(df))) # pick columns for which sum of their elements is at least 10
1-element Vector{String}:
 "x4"

julia> names(df, eltype.(eachcol(df)) .>: Missing) # pick columns that allow missing values
3-element Vector{String}:
 "x1"
 "x3"
 "x4"

julia> names(df, any.(ismissing, eachcol(df))) # pick columns that contain missing values
2-element Vector{String}:
 "x1"
 "x3"
```
