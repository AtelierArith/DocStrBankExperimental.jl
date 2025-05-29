```
@transform(d, i...; kwargs...)
```

Add additional columns or keys based on keyword-like arguments.

### Arguments

  * `d`: an `AbstractDataFrame`, or `GroupedDataFrame`
  * `i...`: transformations defining new columns or keys, of the form `:y = f(:x)`
  * `kwargs...`: keyword arguments passed to `DataFrames.transform`

### Returns

  * `::AbstractDataFrame` or `::GroupedDataFrame`

### Details

Inputs to `@transform` can come in two formats: a `begin ... end` block, in which case each line in the block is a separate transformation, (`:y = f(:x)`), or as a series of keyword-like arguments. For example, the following are equivalent:

```julia
@transform df begin
    :a = :x
    :b = :y
end
```

and

```
@transform(df, :a = :x, :b = :y)
```

`@transform` uses the syntax `@byrow` to wrap transformations in the `ByRow` function wrapper from DataFrames, apply a function row-wise, similar to broadcasting. For example, the call

```
@transform(df, @byrow :y = :x == 1 ? true : false)
```

becomes

```
transform(df, :x => ByRow(x -> x == 1 ? true : false) => :y)
```

a transformation which cannot be conveniently expressed using broadcasting.

To avoid writing `@byrow` multiple times when performing multiple transformations by row, `@transform` allows `@byrow` at the beginning of a block of transformations (i.e. `@byrow begin... end`). All transformations in the block will operate by row.

Transformations can also use the macro-flag [`@astable`](@ref) for creating multiple new columns at once and letting transformations share the same name-space. See `? @astable` for more details.

In operations, it is also allowed to use `AsTable(cols)` to work with multiple columns at once, where the columns are grouped together in a `NamedTuple`. When `AsTable(cols)` appears in a operation, no other columns may be referenced in the block.

Using `AsTable` in this way is useful for working with many columns at once programmatically. For example, to compute the row-wise sum of the columns `[:a, :b, :c, :d]`, write

```
@byrow :c = sum(AsTable([:a, :b, :c, :d]))
```

This constructs the pairs

```
AsTable(nms) => ByRow(sum) => :c
```

`AsTable` on the right-hand side also allows the use of the special column selectors `Not`, `Between`, and regular expressions. For example, to calculate the product of all the columns beginning with the letter `"a"`, write

```
@byrow :d = prod(AsTable(r"^a"))
```

`@transform` accepts the same keyword arguments as `DataFrames.transform!` and can be added in two ways. When inputs are given as multiple arguments, they are added at the end after a semi-colon `;`, as in

```
@transform(gd, :x = :a .- 1; ungroup = false)
```

When inputs are given in "block" format, the last lines may be written `@kwarg key = value`, which indicates keyword arguments to be passed to `transform!` function.

```
@transform gd begin
    :x = :a .- 1
    @kwarg ungroup = false
end
```

### Examples

```jldoctest
julia> using DataFramesMeta

julia> df = DataFrame(A = 1:3, B = [2, 1, 2]);

julia> @transform df begin
           :a = 2 * :A
           :x = :A .+ :B
       end
3×4 DataFrame
 Row │ A      B      a      x
     │ Int64  Int64  Int64  Int64
─────┼────────────────────────────
   1 │     1      2      2      3
   2 │     2      1      4      3
   3 │     3      2      6      5

julia> @transform df @byrow :z = :A * :B
3×3 DataFrame
 Row │ A      B      z
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      2      2
   2 │     2      1      2
   3 │     3      2      6

julia> @transform df @byrow begin
           :x = :A * :B
           :y = :A == 1 ? 100 : 200
       end
3×4 DataFrame
 Row │ A      B      x      y
     │ Int64  Int64  Int64  Int64
─────┼────────────────────────────
   1 │     1      2      2    100
   2 │     2      1      2    200
   3 │     3      2      6    200
```
