```
unstack(df::AbstractDataFrame, rowkeys, colkey, value;
        renamecols::Function=identity, allowmissing::Bool=false,
        combine=only, fill=missing, threads::Bool=true)
unstack(df::AbstractDataFrame, colkey, value;
        renamecols::Function=identity, allowmissing::Bool=false,
        combine=only, fill=missing, threads::Bool=true)
unstack(df::AbstractDataFrame;
        renamecols::Function=identity, allowmissing::Bool=false,
        combine=only, fill=missing, threads::Bool=true)
```

Unstack data frame `df`, i.e. convert it from long to wide format.

Row and column keys are ordered in the order of their first appearance.

# Positional arguments

  * `df` : the AbstractDataFrame to be unstacked
  * `rowkeys` : the columns with a unique key for each row, if not given, find a key by grouping on anything not a `colkey` or `value`. Can be any column selector (`Symbol`, string or integer; `:`, `Cols`, `All`, `Between`, `Not`, a regular expression, or a vector of `Symbol`s, strings or integers). If `rowkeys` contains no columns all rows are assumed to have the same key.
  * `colkey` : the column (`Symbol`, string or integer) holding the column names in wide format, defaults to `:variable`
  * `values` : the column storing values (`Symbol`, string or integer), defaults to `:value`

# Keyword arguments

  * `renamecols`: a function called on each unique value in `colkey`; it must return the name of the column to be created (typically as a string or a `Symbol`). Duplicates in resulting names when converted to `Symbol` are not allowed. By default no transformation is performed.
  * `allowmissing`: if `false` (the default) then an error is thrown if `colkey` contains `missing` values; if `true` then a column referring to `missing` value is created.
  * `combine`: if `only` (the default) then an error is thrown if combination of `rowkeys` and `colkey` contains duplicate entries. Otherwise the passed value must be a function that is called on a vector view containing all elements for each combination of `rowkeys` and `colkey` present in the data.
  * `fill`: missing row/column combinations are filled with this value. The default is `missing`. If the `value` column is a `CategoricalVector` and `fill` is not `missing` then in order to keep unstacked value columns also `CategoricalVector` the `fill` must be passed as `CategoricalValue`
  * `threads`: whether `combine` function may be run in separate tasks which can execute in parallel (possibly being applied to multiple groups at the same time). Whether or not tasks are actually spawned and their number are determined automatically. Set to `false` if `combine` requires serial execution or is not thread-safe.

Metadata: table-level `:note`-style metadata and column-level `:note`-style metadata for row keys columns are preserved.

# Deprecations

  * `allowduplicates` keyword argument is deprecated; instead use `combine` keyword argument; an equivalent to `allowduplicates=true` is `combine=last` and to `allowduplicates=false` is `combine=only` (the default);

# Examples

```jldoctest
julia> wide = DataFrame(id=1:6,
                        a=repeat(1:3, inner=2),
                        b=repeat(1.0:2.0, inner=3),
                        c=repeat(1.0:1.0, inner=6),
                        d=repeat(1.0:3.0, inner=2))
6×5 DataFrame
 Row │ id     a      b        c        d
     │ Int64  Int64  Float64  Float64  Float64
─────┼─────────────────────────────────────────
   1 │     1      1      1.0      1.0      1.0
   2 │     2      1      1.0      1.0      1.0
   3 │     3      2      1.0      1.0      2.0
   4 │     4      2      2.0      1.0      2.0
   5 │     5      3      2.0      1.0      3.0
   6 │     6      3      2.0      1.0      3.0

julia> long = stack(wide)
18×4 DataFrame
 Row │ id     a      variable  value
     │ Int64  Int64  String    Float64
─────┼─────────────────────────────────
   1 │     1      1  b             1.0
   2 │     2      1  b             1.0
   3 │     3      2  b             1.0
   4 │     4      2  b             2.0
   5 │     5      3  b             2.0
   6 │     6      3  b             2.0
   7 │     1      1  c             1.0
   8 │     2      1  c             1.0
  ⋮  │   ⋮      ⋮       ⋮         ⋮
  12 │     6      3  c             1.0
  13 │     1      1  d             1.0
  14 │     2      1  d             1.0
  15 │     3      2  d             2.0
  16 │     4      2  d             2.0
  17 │     5      3  d             3.0
  18 │     6      3  d             3.0
                         3 rows omitted

julia> unstack(long)
6×5 DataFrame
 Row │ id     a      b         c         d
     │ Int64  Int64  Float64?  Float64?  Float64?
─────┼────────────────────────────────────────────
   1 │     1      1       1.0       1.0       1.0
   2 │     2      1       1.0       1.0       1.0
   3 │     3      2       1.0       1.0       2.0
   4 │     4      2       2.0       1.0       2.0
   5 │     5      3       2.0       1.0       3.0
   6 │     6      3       2.0       1.0       3.0

julia> unstack(long, :variable, :value)
6×5 DataFrame
 Row │ id     a      b         c         d
     │ Int64  Int64  Float64?  Float64?  Float64?
─────┼────────────────────────────────────────────
   1 │     1      1       1.0       1.0       1.0
   2 │     2      1       1.0       1.0       1.0
   3 │     3      2       1.0       1.0       2.0
   4 │     4      2       2.0       1.0       2.0
   5 │     5      3       2.0       1.0       3.0
   6 │     6      3       2.0       1.0       3.0

julia> unstack(long, :id, :variable, :value)
6×4 DataFrame
 Row │ id     b         c         d
     │ Int64  Float64?  Float64?  Float64?
─────┼─────────────────────────────────────
   1 │     1       1.0       1.0       1.0
   2 │     2       1.0       1.0       1.0
   3 │     3       1.0       1.0       2.0
   4 │     4       2.0       1.0       2.0
   5 │     5       2.0       1.0       3.0
   6 │     6       2.0       1.0       3.0

julia> unstack(long, [:id, :a], :variable, :value)
6×5 DataFrame
 Row │ id     a      b         c         d
     │ Int64  Int64  Float64?  Float64?  Float64?
─────┼────────────────────────────────────────────
   1 │     1      1       1.0       1.0       1.0
   2 │     2      1       1.0       1.0       1.0
   3 │     3      2       1.0       1.0       2.0
   4 │     4      2       2.0       1.0       2.0
   5 │     5      3       2.0       1.0       3.0
   6 │     6      3       2.0       1.0       3.0

julia> unstack(long, :id, :variable, :value, renamecols=x->Symbol(:_, x))
6×4 DataFrame
 Row │ id     _b        _c        _d
     │ Int64  Float64?  Float64?  Float64?
─────┼─────────────────────────────────────
   1 │     1       1.0       1.0       1.0
   2 │     2       1.0       1.0       1.0
   3 │     3       1.0       1.0       2.0
   4 │     4       2.0       1.0       2.0
   5 │     5       2.0       1.0       3.0
   6 │     6       2.0       1.0       3.0
```

Note that there are some differences between the widened results above.

```jldoctest
julia> df = DataFrame(id=["1", "1", "2"],
                      variable=["Var1", "Var2", "Var1"],
                      value=[1, 2, 3])
3×3 DataFrame
 Row │ id      variable  value
     │ String  String    Int64
─────┼─────────────────────────
   1 │ 1       Var1          1
   2 │ 1       Var2          2
   3 │ 2       Var1          3

julia> unstack(df, :variable, :value, fill=0)
2×3 DataFrame
 Row │ id      Var1   Var2
     │ String  Int64  Int64
─────┼──────────────────────
   1 │ 1           1      2
   2 │ 2           3      0

julia> df = DataFrame(cols=["a", "a", "b"], values=[1, 2, 4])
3×2 DataFrame
 Row │ cols    values
     │ String  Int64
─────┼────────────────
   1 │ a            1
   2 │ a            2
   3 │ b            4

julia> unstack(df, :cols, :values, combine=copy)
1×2 DataFrame
 Row │ a        b
     │ Array…?  Array…?
─────┼──────────────────
   1 │ [1, 2]   [4]

julia> unstack(df, :cols, :values, combine=sum)
1×2 DataFrame
 Row │ a       b
     │ Int64?  Int64?
─────┼────────────────
   1 │      3       4
```
