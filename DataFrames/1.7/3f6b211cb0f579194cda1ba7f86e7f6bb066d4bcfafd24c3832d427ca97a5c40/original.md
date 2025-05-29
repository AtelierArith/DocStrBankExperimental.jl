```
antijoin(df1, df2; on, makeunique=false, validate=(false, false), matchmissing=:error)
```

Perform an anti join of two data frame objects and return a `DataFrame` containing the result. An anti join returns the subset of rows of `df1` that do not match with the keys in `df2`.

The order of rows in the result is kept from `df1`.

# Arguments

  * `df1`, `df2`: the `AbstractDataFrames` to be joined

# Keyword Arguments

  * `on` : The names of the key columns on which to join the data frames. This can be a single name, or a vector of names (for joining on multiple columns). A `left=>right` pair of names can be used instead of a name, for the case where a key has different names in `df1` and `df2` (it is allowed to mix names and name pairs in a vector). Key values are compared using `isequal`. `on` is a required argument.
  * `makeunique` : ignored as no columns are added to `df1` columns (it is provided for consistency with other functions).
  * `validate` : whether to check that columns passed as the `on` argument  define unique keys in each input data frame (according to `isequal`).  Can be a tuple or a pair, with the first element indicating whether to  run check for `df1` and the second element for `df2`.  By default no check is performed.
  * `matchmissing` : if equal to `:error` throw an error if `missing` is present in `on` columns; if equal to `:equal` then `missing` is allowed and missings are matched; if equal to `:notequal` then missings are dropped in `df2` `on` columns.

It is not allowed to join on columns that contain `NaN` or `-0.0` in real or imaginary part of the number. If you need to perform a join on such values use CategoricalArrays.jl and transform a column containing such values into a `CategoricalVector`.

When merging `on` categorical columns that differ in the ordering of their levels, the ordering of the left data frame takes precedence over the ordering of the right data frame.

Metadata: table-level and column-level `:note`-style metadata are taken from `df1`.

See also: [`innerjoin`](@ref), [`leftjoin`](@ref), [`rightjoin`](@ref),           [`outerjoin`](@ref), [`semijoin`](@ref), [`crossjoin`](@ref).

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

julia> antijoin(name, job, on = :ID)
1×2 DataFrame
 Row │ ID     Name
     │ Int64  String
─────┼──────────────────
   1 │     3  Joe Blogs

julia> job2 = DataFrame(identifier=[1, 2, 4], Job=["Lawyer", "Doctor", "Farmer"])
3×2 DataFrame
 Row │ identifier  Job
     │ Int64       String
─────┼────────────────────
   1 │          1  Lawyer
   2 │          2  Doctor
   3 │          4  Farmer

julia> antijoin(name, job2, on = :ID => :identifier)
1×2 DataFrame
 Row │ ID     Name
     │ Int64  String
─────┼──────────────────
   1 │     3  Joe Blogs

julia> antijoin(name, job2, on = [:ID => :identifier])
1×2 DataFrame
 Row │ ID     Name
     │ Int64  String
─────┼──────────────────
   1 │     3  Joe Blogs
```
