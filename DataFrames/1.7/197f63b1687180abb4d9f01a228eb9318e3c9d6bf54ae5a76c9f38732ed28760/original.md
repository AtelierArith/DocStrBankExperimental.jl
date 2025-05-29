```
leftjoin(df1, df2; on, makeunique=false, source=nothing, validate=(false, false),
         renamecols=(identity => identity), matchmissing=:error, order=:undefined)
```

Perform a left join of two data frame objects and return a `DataFrame` containing the result. A left join includes all rows from `df1`.

In the returned data frame the type of the columns on which the data frames are joined is determined by the type of these columns in `df1`. This behavior may change in future releases.

# Arguments

  * `df1`, `df2`: the `AbstractDataFrames` to be joined

# Keyword Arguments

  * `on` : The names of the key columns on which to join the data frames. This can be a single name, or a vector of names (for joining on multiple columns). A `left=>right` pair of names can be used instead of a name, for the case where a key has different names in `df1` and `df2` (it is allowed to mix names and name pairs in a vector). Key values are compared using `isequal`. `on` is a required argument.
  * `makeunique` : if `false` (the default), an error will be raised if duplicate names are found in columns not joined on; if `true`, duplicate names will be suffixed with `_i` (`i` starting at 1 for the first duplicate).
  * `source` : Default: `nothing`. If a `Symbol` or string, adds indicator column with the given name, for whether a row appeared in only `df1` (`"left_only"`) or in both (`"both"`). If the name is already in use, the column name will be modified if `makeunique=true`.
  * `validate` : whether to check that columns passed as the `on` argument define unique keys in each input data frame (according to `isequal`). Can be a tuple or a pair, with the first element indicating whether to run check for `df1` and the second element for `df2`. By default no check is performed.
  * `renamecols` : a `Pair` specifying how columns of left and right data frames should be renamed in the resulting data frame. Each element of the pair can be a string or a `Symbol` can be passed in which case it is appended to the original column name; alternatively a function can be passed in which case it is applied to each column name, which is passed to it as a `String`. Note that `renamecols` does not affect `on` columns, whose names are always taken from the left data frame and left unchanged.
  * `matchmissing` : if equal to `:error` throw an error if `missing` is present in `on` columns; if equal to `:equal` then `missing` is allowed and missings are matched; if equal to `:notequal` then missings are dropped in `df2` `on` columns.
  * `order` : if `:undefined` (the default) the order of rows in the result is  undefined and may change in future releases. If `:left` then the order of  rows from the left data frame is retained. If `:right` then the order of rows  from the right data frame is retained (non-matching rows are put at the end).

All columns of the returned data frame will support missing values.

It is not allowed to join on columns that contain `NaN` or `-0.0` in real or imaginary part of the number. If you need to perform a join on such values use CategoricalArrays.jl and transform a column containing such values into a `CategoricalVector`.

When merging `on` categorical columns that differ in the ordering of their levels, the ordering of the left data frame takes precedence over the ordering of the right data frame.

Metadata: table-level and column-level `:note`-style metadata is taken from `df1` (including key columns), except for columns added to it from `df2`, whose column-level `:note`-style metadata is taken from `df2`.

See also: [`innerjoin`](@ref), [`rightjoin`](@ref), [`outerjoin`](@ref),           [`semijoin`](@ref), [`antijoin`](@ref), [`crossjoin`](@ref).

# Examples

```jldoctest
julia> name = DataFrame(ID=[1, 2, 3], Name=["John Doe", "Jane Doe", "Joe Blogs"])
3×2 DataFrame
 Row │ ID     Name
     │ Int64  String
─────┼──────────────────
   1 │     1  John Doe
   2 │     2  Jane Doe
   3 │     3  Joe Blogs

julia> job = DataFrame(ID=[1, 2, 4], Job=["Lawyer", "Doctor", "Farmer"])
3×2 DataFrame
 Row │ ID     Job
     │ Int64  String
─────┼───────────────
   1 │     1  Lawyer
   2 │     2  Doctor
   3 │     4  Farmer

julia> leftjoin(name, job, on = :ID)
3×3 DataFrame
 Row │ ID     Name       Job
     │ Int64  String     String?
─────┼───────────────────────────
   1 │     1  John Doe   Lawyer
   2 │     2  Jane Doe   Doctor
   3 │     3  Joe Blogs  missing

julia> job2 = DataFrame(identifier=[1, 2, 4], Job=["Lawyer", "Doctor", "Farmer"])
3×2 DataFrame
 Row │ identifier  Job
     │ Int64       String
─────┼────────────────────
   1 │          1  Lawyer
   2 │          2  Doctor
   3 │          4  Farmer

julia> leftjoin(name, job2, on = :ID => :identifier, renamecols = "_left" => "_right")
3×3 DataFrame
 Row │ ID     Name_left  Job_right
     │ Int64  String     String?
─────┼─────────────────────────────
   1 │     1  John Doe   Lawyer
   2 │     2  Jane Doe   Doctor
   3 │     3  Joe Blogs  missing

julia> leftjoin(name, job2, on = [:ID => :identifier], renamecols = uppercase => lowercase)
3×3 DataFrame
 Row │ ID     NAME       job
     │ Int64  String     String?
─────┼───────────────────────────
   1 │     1  John Doe   Lawyer
   2 │     2  Jane Doe   Doctor
   3 │     3  Joe Blogs  missing
```
