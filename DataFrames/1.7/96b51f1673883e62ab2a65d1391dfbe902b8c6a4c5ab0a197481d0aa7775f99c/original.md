```
describe(df::AbstractDataFrame; cols=:)
describe(df::AbstractDataFrame, stats::Union{Symbol, Pair}...; cols=:)
```

Return descriptive statistics for a data frame as a new `DataFrame` where each row represents a variable and each column a summary statistic.

# Arguments

  * `df` : the `AbstractDataFrame`
  * `stats::Union{Symbol, Pair}...` : the summary statistics to report. Arguments can be:

      * A symbol from the list `:mean`, `:std`, `:min`, `:q25`, `:median`, `:q75`, `:max`, `:sum`, `:eltype`, `:nunique`, `:nuniqueall`, `:first`, `:last`, `:nnonmissing`, and `:nmissing`. The default statistics used are `:mean`, `:min`, `:median`, `:max`, `:nmissing`, and `:eltype`.
      * `:detailed` as the only `Symbol` argument to return all statistics except `:first`, `:last`, `:sum`, `:nuniqueall`, and `:nnonmissing`.
      * `:all` as the only `Symbol` argument to return all statistics.
      * A `function => name` pair where `name` is a `Symbol` or string. This will create a column of summary statistics with the provided name.
  * `cols` : a keyword argument allowing to select only a subset or transformation of columns from `df` to describe. Can be any column selector or transformation accepted by [`select`](@ref).

# Details

For `Real` columns, compute the mean, standard deviation, minimum, first quantile, median, third quantile, and maximum. If a column does not derive from `Real`, `describe` will attempt to calculate all statistics, using `nothing` as a fall-back in the case of an error.

When `stats` contains `:nunique`, `describe` will report the number of unique values in a column. If a column's base type derives from `Real`, `:nunique` will return `nothing`s. Use `:nuniqueall` to report the number of unique values in all columns.

Missing values are filtered in the calculation of all statistics, however the column `:nmissing` will report the number of missing values of that variable and `:nnonmissing` the number of non-missing values.

If custom functions are provided, they are called repeatedly with the vector corresponding to each column as the only argument. For columns allowing for missing values, the vector is wrapped in a call to `skipmissing`: custom functions must therefore support such objects (and not only vectors), and cannot access missing values.

Metadata: this function drops all metadata.

# Examples

```jldoctest
julia> df = DataFrame(i=1:10, x=0.1:0.1:1.0, y='a':'j');

julia> describe(df)
3×7 DataFrame
 Row │ variable  mean    min  median  max  nmissing  eltype
     │ Symbol    Union…  Any  Union…  Any  Int64     DataType
─────┼────────────────────────────────────────────────────────
   1 │ i         5.5     1    5.5     10          0  Int64
   2 │ x         0.55    0.1  0.55    1.0         0  Float64
   3 │ y                 a            j           0  Char

julia> describe(df, :min, :max)
3×3 DataFrame
 Row │ variable  min  max
     │ Symbol    Any  Any
─────┼────────────────────
   1 │ i         1    10
   2 │ x         0.1  1.0
   3 │ y         a    j

julia> describe(df, :min, sum => :sum)
3×3 DataFrame
 Row │ variable  min  sum
     │ Symbol    Any  Union…
─────┼───────────────────────
   1 │ i         1    55
   2 │ x         0.1  5.5
   3 │ y         a

julia> describe(df, :min, sum => :sum, cols=:x)
1×3 DataFrame
 Row │ variable  min      sum
     │ Symbol    Float64  Float64
─────┼────────────────────────────
   1 │ x             0.1      5.5
```
