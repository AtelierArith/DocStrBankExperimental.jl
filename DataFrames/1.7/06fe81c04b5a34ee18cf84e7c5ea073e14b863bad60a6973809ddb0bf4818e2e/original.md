```
crossjoin(df1::AbstractDataFrame, df2::AbstractDataFrame;
          makeunique::Bool=false, renamecols=identity => identity)
crossjoin(df1, df2, dfs...; makeunique = false)
```

Perform a cross join of two or more data frame objects and return a `DataFrame` containing the result. A cross join returns the cartesian product of rows from all passed data frames, where the first passed data frame is assigned to the dimension that changes the slowest and the last data frame is assigned to the dimension that changes the fastest.

# Arguments

  * `df1`, `df2`, `dfs...` : the `AbstractDataFrames` to be joined

# Keyword Arguments

  * `makeunique` : if `false` (the default), an error will be raised if duplicate names are found in columns not joined on; if `true`, duplicate names will be suffixed with `_i` (`i` starting at 1 for the first duplicate).
  * `renamecols` : a `Pair` specifying how columns of left and right data frames should be renamed in the resulting data frame. Each element of the pair can be a string or a `Symbol` can be passed in which case it is appended to the original column name; alternatively a function can be passed in which case it is applied to each column name, which is passed to it as a `String`.

If more than two data frames are passed, the join is performed recursively with left associativity.

Metadata: table-level `:note`-style metadata is preserved only for keys which are defined in all passed tables and have the same value. Column-level `:note`-style metadata is preserved from both tables.

See also: [`innerjoin`](@ref), [`leftjoin`](@ref), [`rightjoin`](@ref),           [`outerjoin`](@ref), [`semijoin`](@ref), [`antijoin`](@ref).

# Examples

```jldoctest
julia> df1 = DataFrame(X=1:3)
3×1 DataFrame
 Row │ X
     │ Int64
─────┼───────
   1 │     1
   2 │     2
   3 │     3

julia> df2 = DataFrame(Y=["a", "b"])
2×1 DataFrame
 Row │ Y
     │ String
─────┼────────
   1 │ a
   2 │ b

julia> crossjoin(df1, df2)
6×2 DataFrame
 Row │ X      Y
     │ Int64  String
─────┼───────────────
   1 │     1  a
   2 │     1  b
   3 │     2  a
   4 │     2  b
   5 │     3  a
   6 │     3  b
```
