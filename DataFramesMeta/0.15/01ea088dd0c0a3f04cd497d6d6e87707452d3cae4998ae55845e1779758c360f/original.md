```
@passmissing(args...)
```

Propagate missing values inside DataFramesMeta.jl macros.

`@passmissing` is not a "real" Julia macro but rather serves as a "flag" to indicate that the anonymous function created by DataFramesMeta.jl to represent an operation should be wrapped in `passmissing` from Missings.jl.

`@passmissing` can only be combined with `@byrow` or the row-wise versions of macros such as `@rtransform` and `@rselect`, etc. If any of the arguments passed to the row-wise anonymous function created by DataFramesMeta.jl with `@byrow`, the result will automatically be `missing`.

In the below example, `@transform` would throw an error without the `@passmissing` flag.

`@passmissing` is especially useful for functions which operate on strings, such as `parse`.

### Examples

```
julia> no_missing(x::Int, y::Int) = x + y;

julia> df = DataFrame(a = [1, 2, missing], b = [4, 5, 6])
3×2 DataFrame
 Row │ a        b
     │ Int64?   Int64
─────┼────────────────
   1 │       1      4
   2 │       2      5
   3 │ missing      6

julia> @transform df @passmissing @byrow c = no_missing(:a, :b)
3×3 DataFrame
 Row │ a        b      c
     │ Int64?   Int64  Int64?
─────┼─────────────────────────
   1 │       1      4        5
   2 │       2      5        7
   3 │ missing      6  missing

julia> df = DataFrame(x_str = ["1", "2", missing])
3×1 DataFrame
 Row │ x_str
     │ String?
─────┼─────────
   1 │ 1
   2 │ 2
   3 │ missing

julia> @rtransform df @passmissing x = parse(Int, :x_str)
3×2 DataFrame
 Row │ x_str    x
     │ String?  Int64?
─────┼──────────────────
   1 │ 1              1
   2 │ 2              2
   3 │ missing  missing
```
