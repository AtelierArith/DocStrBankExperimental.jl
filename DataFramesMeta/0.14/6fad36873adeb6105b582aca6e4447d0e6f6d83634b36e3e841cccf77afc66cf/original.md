```
@subset(d, i...; kwargs...)
```

Select row subsets in `AbstractDataFrame`s and `GroupedDataFrame`s.

### Arguments

  * `d` : an AbstractDataFrame or GroupedDataFrame
  * `i...` : expression for selecting rows
  * `kwargs...` : keyword arguments passed to `DataFrames.subset`

### Details

Multiple `i` expressions are "and-ed" together.

If given a `GroupedDataFrame`, `@subset` applies transformations by group, and returns a fresh `DataFrame` containing the rows for which the generated values are all `true`.

Inputs to `@subset` can come in two formats: a `begin ... end` block, in which case each line is a separate selector, or as multiple arguments. For example the following two statements are equivalent:

```julia
@subset df begin
    :x .> 1
    :y .< 2
end
```

and

```
@subset(df, :x .> 1, :y .< 2)
```

!!! note
    `@subset` treats `missing` values as `false` when filtering rows. Unlike `DataFrames.subset` and other Boolean operations with `missing`, `@subset` will *not* error on missing values, and will only keep `true` values.


If an expression provided to `@subset` begins with `@byrow`, operations are applied "by row" along the data frame. To avoid writing `@byrow` multiple times, `@orderby` also allows `@byrow` to be placed at the beginning of a block of operations. For example, the following two statements are equivalent.

```
@subset df @byrow begin
    :x > 1
    :y < 2
end
```

and

```
@subset df
    @byrow :x > 1
    @byrow :y < 2
end
```

In operations, it is also allowed to use `AsTable(cols)` to work with multiple columns at once, where the columns are grouped together in a `NamedTuple`. When `AsTable(cols)` appears in a operation, no other columns may be referenced in the block.

Using `AsTable` in this way is useful for working with many columns at once programmatically. For example, to select rows where the sum of the columns `:a`, `:b`, and `:c` is greater than `5`, write

```
@byrow sum(AsTable([:a, :b, :c])) > 5
```

This constructs the pair

```
AsTable([:a, :b, :c]) => ByRow(t -> sum(t) > 5)
```

`AsTable` on the right-hand side also allows the use of the special column selectors `Not`, `Between`, and regular expressions. For example, to subset all rows where the product of all columns starting with `"a"`, is greater than `5`, write

```
@byrow prod(AsTable(r"^a")) > 5
```

`@subset` accepts the same keyword arguments as `DataFrames.subset` and can be added in two ways. When inputs are given as multiple arguments, they are added at the end after a semi-colon `;`, as in

```
@subset(df, :a; skipmissing = false, view = true)
```

When inputs are given in "block" format, the last lines may be written `@kwarg key = value`, which indicates keyword arguments to be passed to `subset` function.

```
@subset df begin
    :a .== 1
    @kwarg skipmissing = false
    @kwarg view = true
end
```

### Examples

```jldoctest
julia> using DataFramesMeta, Statistics

julia> df = DataFrame(x = 1:3, y = [2, 1, 2]);

julia> globalvar = [2, 1, 0];

julia> @subset(df, :x .> 1)
2×2 DataFrame
 Row │ x      y
     │ Int64  Int64
─────┼──────────────
   1 │     2      1
   2 │     3      2

julia> @subset(df, :x .> globalvar)
2×2 DataFrame
 Row │ x      y
     │ Int64  Int64
─────┼──────────────
   1 │     2      1
   2 │     3      2

julia> @subset df begin
           :x .> globalvar
           :y .== 3
       end
0×2 DataFrame

julia> df = DataFrame(n = 1:20, x = [3, 3, 3, 3, 1, 1, 1, 2, 1, 1,
                                    2, 1, 1, 2, 2, 2, 3, 1, 1, 2]);

julia> g = groupby(df, :x);

julia> @subset(g, :n .> mean(:n))
8×2 DataFrame
 Row │ n      x
     │ Int64  Int64
─────┼──────────────
   1 │    12      1
   2 │    13      1
   3 │    15      2
   4 │    16      2
   5 │    17      3
   6 │    18      1
   7 │    19      1
   8 │    20      2

julia> @subset g begin
           :n .> mean(:n)
           :n .< 20
       end
7×2 DataFrame
 Row │ n      x
     │ Int64  Int64
─────┼──────────────
   1 │    12      1
   2 │    13      1
   3 │    15      2
   4 │    16      2
   5 │    17      3
   6 │    18      1
   7 │    19      1

julia> df = DataFrame(a = [1, 2, missing], b = ["x", "y", missing]);

julia> @subset(df, :a .== 1)
1×2 DataFrame
 Row │ a       b
     │ Int64?  String?
─────┼─────────────────
   1 │      1  x

julia> @subset(df, :a .< 3; view = true)
2×2 SubDataFrame
 Row │ a       b
     │ Int64?  String?
─────┼─────────────────
   1 │      1  x
   2 │      2  y

julia> @subset df begin
           :a .< 3
           @kwarg view = true
       end
2×2 SubDataFrame
 Row │ a       b
     │ Int64?  String?
─────┼─────────────────
   1 │      1  x
   2 │      2  y
```
