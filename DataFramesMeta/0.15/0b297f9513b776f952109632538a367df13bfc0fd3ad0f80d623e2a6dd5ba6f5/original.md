```
@combine(x, args...; kwargs...)
```

Summarize a grouping operation

### Arguments

  * `x` : a `GroupedDataFrame` or `AbstractDataFrame`
  * `args...` : transformations defining new columns, of the form `:y = f(:x)`
  * `kwargs`: : keyword arguments passed to `DataFrames.combine`

### Results

  * A `DataFrame` or a `GroupedDataFrame`

### Details

Inputs to `@combine` can come in two formats: a `begin ... end` block, in which case each line in the block is a separate transformation, or as a series of keyword-like arguments. For example, the following are equivalent:

```
@combine df begin
    :mx = mean(:x)
    :sx = std(:x)
end
```

and

```
@combine(df, :mx = mean(:x), :sx = std(:x))
```

Transformations can also use the macro-flag [`@astable`](@ref) for creating multiple new columns at once and letting transformations share the same name-space. See `? @astable` for more details.

`@combine` accepts the same keyword arguments as `DataFrames.combine` and can be added in two ways. When inputs are given as multiple arguments, they are added at the end after a semi-colon `;`, as in

```
@combine(gd, :x = first(:a); ungroup = false)
```

When inputs are given in "block" format, the last lines may be written `@kwarg key = value`, which indicates keyword arguments to be passed to `combine` function.

```
@combine gd begin
    :x = first(:a)
    @kwarg ungroup = false
end
```

### Examples

```julia
julia> using DataFramesMeta

julia> d = DataFrame(
            n = 1:20,
            x = [3, 3, 3, 3, 1, 1, 1, 2, 1, 1, 2, 1, 1, 2, 2, 2, 3, 1, 1, 2]);

julia> g = groupby(d, :x);

julia> @combine(g, :nsum = sum(:n))
3×2 DataFrame
 Row │ x      nsum
     │ Int64  Int64
─────┼──────────────
   1 │     1     99
   2 │     2     84
   3 │     3     27

julia> @combine g begin
           :x2 = 2 * :x
           :nsum = sum(:n)
       end
20×3 DataFrame
 Row │ x      x2     nsum
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      2     99
   2 │     1      2     99
   3 │     1      2     99
   4 │     1      2     99
   5 │     1      2     99
   6 │     1      2     99
   7 │     1      2     99
   8 │     1      2     99
   9 │     1      2     99
  10 │     2      4     84
  11 │     2      4     84
  12 │     2      4     84
  13 │     2      4     84
  14 │     2      4     84
  15 │     2      4     84
  16 │     3      6     27
  17 │     3      6     27
  18 │     3      6     27
  19 │     3      6     27
  20 │     3      6     27

```
