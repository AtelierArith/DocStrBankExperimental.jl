```
@select!(d, i...; kwargs...)
```

Mutate `d` in-place to retain only columns or transformations specified by `e` and return it. No copies of existing columns are made.

### Arguments

  * `d` : an AbstractDataFrame
  * `i` : transformations of the form `:y = f(:x)` specifying

new columns in terms of existing columns or symbols to specify existing columns

  * `kwargs` : keyword arguments passed to `DataFrames.select!`

### Returns

  * `::DataFrame`

### Details

Inputs to `@select!` can come in two formats: a `begin ... end` block, in which case each line in the block is a separate transformation or selector, or as a series of arguments and keyword-like arguments. For example, the following are equivalent:

`@select!` uses the syntax `@byrow` to wrap transformations in the `ByRow` function wrapper from DataFrames, apply a function row-wise, similar to broadcasting. For example, the call

```
@select!(df, @byrow :y = :x == 1 ? true : false)
```

becomes

```
select!(df, :x => ByRow(x -> x == 1 ? true : false) => :y)
```

a transformation which cannot be conveniently expressed using broadcasting.

To avoid writing `@byrow` multiple times when performing multiple transformations by row, `@select!` allows `@byrow` at the beginning of a block of select!ations (i.e. `@byrow begin... end`). All transformations in the block will operate by row.

To select many columns at once use the tools `Not`, `Between`, `All`, and `Cols`.

  * `@select df Not(:a)` keeps all columns except for `:a`
  * `@select df Between(:a, :z)` keeps all columns between `:a` and `:z`, inclusive
  * `@select df All()` keeps all columns
  * `@select df Cols(...)` can be used to combine many different selectors, as well as use regular expressions. For example `Cols(r"a")` selects all columns that start with `"a"`.

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

`@select!` accepts the same keyword arguments as `DataFrames.select!` and can be added in two ways. When inputs are given as multiple arguments, they are added at the end after a semi-colon `;`, as in

```
@select!(gd, :a; ungroup = false)
```

When inputs are given in "block" format, the last lines may be written `@kwarg key = value`, which indicates keyword arguments to be passed to `select!` function.

```
@select! gd begin
    :a
    @kwarg ungroup = false
end
```

### Examples

```jldoctest
julia> using DataFrames, DataFramesMeta

julia> df = DataFrame(a = repeat(1:4, outer = 2), b = repeat(2:-1:1, outer = 4), c = 1:8);

julia> df2 = @select!(df, :c, :a)
8×2 DataFrame
 Row │ c      a
     │ Int64  Int64
─────┼──────────────
   1 │     1      1
   2 │     2      2
   3 │     3      3
   4 │     4      4
   5 │     5      1
   6 │     6      2
   7 │     7      3
   8 │     8      4

julia> df === df2
true

julia> df = DataFrame(a = repeat(1:4, outer = 2), b = repeat(2:-1:1, outer = 4), c = 1:8);

julia> df2 = @select! df begin
           :c
           :x = :b + :c
       end
8×2 DataFrame
 Row │ c      x
     │ Int64  Int64
─────┼──────────────
   1 │     1      3
   2 │     2      3
   3 │     3      5
   4 │     4      5
   5 │     5      7
   6 │     6      7
   7 │     7      9
   8 │     8      9

julia> df === df2
true
```
