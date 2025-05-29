```
@by(d::AbstractDataFrame, cols, e...; kwargs...)
```

Split-apply-combine in one step.

### Arguments

  * `d` : an AbstractDataFrame
  * `cols` : a column indicator (Symbol, Int, Vector{Symbol}, etc.)
  * `e` :  keyword-like arguments, of the form `:y = f(:x)` specifying

new columns in terms of column groupings

  * `kwargs` : keyword arguments passed to `DataFrames.combine`

### Returns

  * `::DataFrame` or a `GroupedDataFrame`

### Details

Transformation inputs to `@by` can come in two formats: a `begin ... end` block, in which case each line in the block is a separate transformation, or as a series of keyword-like arguments. For example, the following are equivalent:

```
@by df :g begin
    :mx = mean(:x)
    :sx = std(:x)
end
```

and

```
@by(df, :g, mx = mean(:x), sx = std(:x))
```

Transformations can also use the macro-flag [`@astable`](@ref) for creating multiple new columns at once and letting transformations share the same name-space. See `? @astable` for more details.

`@by` accepts the same keyword arguments as `DataFrames.combine` and can be added in two ways. When inputs are given as multiple arguments, they are added at the end after a semi-colon `;`, as in

```
@by(ds, :g, :x = first(:a); ungroup = false)
```

When inputs are given in "block" format, the last lines may be written `@kwarg key = value`, which indicates keyword arguments to be passed to `combine` function.

```
@by df :a begin
    :x = first(:a)
    @kwarg ungroup = false
end
```

Though `@by` performs both `groupby` and `combine`, `@by` only forwards keyword arguments to `combine`, and not `groupby`. To pass keyword arguments to `groupby`, perform the `groupby` and `@combine` steps separately.

### Examples

```julia
julia> using DataFramesMeta, Statistics

julia> df = DataFrame(
            a = repeat(1:4, outer = 2),
            b = repeat(2:-1:1, outer = 4),
            c = 1:8);

julia> @by(df, :a, :d = sum(:c))
4×2 DataFrame
 Row │ a      d
     │ Int64  Int64
─────┼──────────────
   1 │     1      6
   2 │     2      8
   3 │     3     10
   4 │     4     12

julia> @by df :a begin
           :d = 2 * :c
       end
8×2 DataFrame
 Row │ a      d
     │ Int64  Int64
─────┼──────────────
   1 │     1      2
   2 │     1     10
   3 │     2      4
   4 │     2     12
   5 │     3      6
   6 │     3     14
   7 │     4      8
   8 │     4     16

julia> @by(df, :a, :c_sum = sum(:c), :c_mean = mean(:c))
4×3 DataFrame
 Row │ a      c_sum  c_mean
     │ Int64  Int64  Float64
─────┼───────────────────────
   1 │     1      6      3.0
   2 │     2      8      4.0
   3 │     3     10      5.0
   4 │     4     12      6.0

julia> @by df :a begin
           :c = :c
           :c_mean = mean(:c)
       end
8×3 DataFrame
 Row │ a      c      c_mean
     │ Int64  Int64  Float64
─────┼───────────────────────
   1 │     1      1      3.0
   2 │     1      5      3.0
   3 │     2      2      4.0
   4 │     2      6      4.0
   5 │     3      3      5.0
   6 │     3      7      5.0
   7 │     4      4      6.0
   8 │     4      8      6.0

```
