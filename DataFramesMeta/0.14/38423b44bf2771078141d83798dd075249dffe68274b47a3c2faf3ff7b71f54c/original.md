```
@orderby(d, i...)
```

Sort rows by values in one of several columns or a transformation of columns. Always returns a fresh `DataFrame`. Does not accept a `GroupedDataFrame`.

### Arguments

  * `d`: a `DataFrame` or `GroupedDataFrame`
  * `i...`: arguments on which to sort the object

### Details

When given a `DataFrame`, `@orderby` applies the transformation given by its arguments (but does not create new columns) and sorts the given `DataFrame` on the result, returning a new `DataFrame`.

Inputs to `@orderby` can come in two formats: a `begin ... end` block, in which case each line in the block is a separate ordering operation, and as mulitple arguments. For example, the following two statements are equivalent:

```julia
@orderby df begin
    :x
    -:y
end
```

and

```
@orderby(df, :x, -:y)
```

### Arguments

  * `d` : an AbstractDataFrame
  * `i...` : expression for sorting

If an expression provided to `@orderby` begins with `@byrow`, operations are applied "by row" along the data frame. To avoid writing `@byrow` multiple times, `@orderby` also allows `@byrow`to be placed at the beginning of a block of operations. For example, the following two statements are equivalent.

```
@orderby df @byrow begin
    :x^2
    :x^3
end
```

and

```
@orderby df
    @byrow :x^2
    @byrow :x^3
end
```

In operations, it is also allowed to use `AsTable(cols)` to work with multiple columns at once, where the columns are grouped together in a `NamedTuple`. When `AsTable(cols)` appears in a operation, no other columns may be referenced in the block.

Using `AsTable` in this way is useful for working with many columns at once programmatically. For example, to order rows by the sum of the columns `:a`, `:b`, and `:c`, write

```
@byrow sum(AsTable([:a, :b, :c]))
```

This constructs the pair

```
AsTable([:a, :b, :c]) => ByRow(sum)
```

`AsTable` on the right-hand side also allows the use of the special column selectors `Not`, `Between`, and regular expressions. For example, to order all rows by the product of all columns starting with `"a"`, write

```
@byrow prod(AsTable(r"^a"))
```

### Examples

```jldoctest
julia> using DataFramesMeta, Statistics

julia> d = DataFrame(x = [3, 3, 3, 2, 1, 1, 1, 2, 1, 1], n = 1:10,
                     c = ["a", "c", "b", "e", "d", "g", "f", "i", "j", "h"]);

julia> @orderby(d, -:n)
10×3 DataFrame
 Row │ x      n      c
     │ Int64  Int64  String
─────┼──────────────────────
   1 │     1     10  h
   2 │     1      9  j
   3 │     2      8  i
   4 │     1      7  f
   5 │     1      6  g
   6 │     1      5  d
   7 │     2      4  e
   8 │     3      3  b
   9 │     3      2  c
  10 │     3      1  a

julia> @orderby(d, invperm(sortperm(:c, rev = true)))
10×3 DataFrame
 Row │ x      n      c
     │ Int64  Int64  String
─────┼──────────────────────
   1 │     1      9  j
   2 │     2      8  i
   3 │     1     10  h
   4 │     1      6  g
   5 │     1      7  f
   6 │     2      4  e
   7 │     1      5  d
   8 │     3      2  c
   9 │     3      3  b
  10 │     3      1  a

julia> @orderby d begin
           :x
           abs.(:n .- mean(:n))
       end
10×3 DataFrame
 Row │ x      n      c
     │ Int64  Int64  String
─────┼──────────────────────
   1 │     1      5  e
   2 │     1      6  f
   3 │     1      7  g
   4 │     1      9  i
   5 │     1     10  j
   6 │     2      4  d
   7 │     2      8  h
   8 │     3      3  c
   9 │     3      2  b
  10 │     3      1  a

julia> @orderby d @byrow :x^2
10×3 DataFrame
 Row │ x      n      c
     │ Int64  Int64  String
─────┼──────────────────────
   1 │     1      5  e
   2 │     1      6  f
   3 │     1      7  g
   4 │     1      9  i
   5 │     1     10  j
   6 │     2      4  d
   7 │     2      8  h
   8 │     3      1  a
   9 │     3      2  b
  10 │     3      3  c
```
