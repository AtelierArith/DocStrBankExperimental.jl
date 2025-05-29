```
leftjoin!(df1, df2; on, makeunique=false, source=nothing,
          matchmissing=:error)
```

Perform a left join of two data frame objects by updating the `df1` with the joined columns from `df2`.

A left join includes all rows from `df1` and leaves all rows and columns from `df1` untouched. Note that each row in `df1` must have at most one match in `df2`. Otherwise, this function would not be able to execute the join in-place since new rows would need to be added to `df1`.

# Arguments

  * `df1`, `df2`: the `AbstractDataFrames` to be joined

# Keyword Arguments

  * `on` : The names of the key columns on which to join the data frames. This can be a single name, or a vector of names (for joining on multiple columns). A `left=>right` pair of names can be used instead of a name, for the case where a key has different names in `df1` and `df2` (it is allowed to mix names and name pairs in a vector). Key values are compared using `isequal`. `on` is a required argument.
  * `makeunique` : if `false` (the default), an error will be raised if duplicate names are found in columns not joined on; if `true`, duplicate names will be suffixed with `_i` (`i` starting at 1 for the first duplicate).
  * `source` : Default: `nothing`. If a `Symbol` or string, adds indicator column with the given name, for whether a row appeared in only `df1` (`"left_only"`) or in both (`"both"`). If the name is already in use, the column name will be modified if `makeunique=true`.
  * `matchmissing` : if equal to `:error` throw an error if `missing` is present in `on` columns; if equal to `:equal` then `missing` is allowed and missings are matched; if equal to `:notequal` then missings are dropped in `df2` `on` columns.

The columns added to `df1` from `df2` will support missing values.

It is not allowed to join on columns that contain `NaN` or `-0.0` in real or imaginary part of the number. If you need to perform a join on such values use CategoricalArrays.jl and transform a column containing such values into a `CategoricalVector`.

Metadata: table-level and column-level `:note`-style metadata are taken from `df1` (including key columns), except for columns added to it from `df2`, whose column-level `:note`-style metadata is taken from `df2`.

See also: [`leftjoin`](@ref).

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

julia> leftjoin!(name, job, on = :ID)
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

julia> leftjoin!(name, job2, on = :ID => :identifier, makeunique=true, source=:source)
3×5 DataFrame
 Row │ ID     Name       Job      Job_1    source
     │ Int64  String     String?  String?  String
─────┼───────────────────────────────────────────────
   1 │     1  John Doe   Lawyer   Lawyer   both
   2 │     2  Jane Doe   Doctor   Doctor   both
   3 │     3  Joe Blogs  missing  missing  left_only
```
