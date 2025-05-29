```
@rorderby(d, args...)
```

Row-wise version of `@orderby`, i.e. all operations use `@byrow` by default. See [`@orderby`](@ref) for details.

Use this function as an alternative to placing the `.` to broadcast row-wise operations.

### Examples

```jldoctest
julia> using DataFramesMeta

julia> df = DataFrame(x = [8,8,-8,7,7,-7], y = [-1, 1, -2, 2, -3, 3])
6×2 DataFrame
 Row │ x      y
     │ Int64  Int64
─────┼──────────────
   1 │     8     -1
   2 │     8      1
   3 │    -8     -2
   4 │     7      2
   5 │     7     -3
   6 │    -7      3

julia> @rorderby df abs(:x) (:x * :y^3)
 Row │ x      y
     │ Int64  Int64
─────┼──────────────
   1 │     7     -3
   2 │    -7      3
   3 │     7      2
   4 │     8     -1
   5 │     8      1
   6 │    -8     -2

julia>  @rorderby df :y == 2 ? -:x : :y
6×2 DataFrame
 Row │ x      y
     │ Int64  Int64
─────┼──────────────
   1 │     7      2
   2 │     7     -3
   3 │    -8     -2
   4 │     8     -1
   5 │     8      1
   6 │    -7      3
```
