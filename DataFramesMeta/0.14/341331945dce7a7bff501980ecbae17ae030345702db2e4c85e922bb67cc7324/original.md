```
@rsubset(d, i...; kwargs...)
```

Row-wise version of `@subset`, i.e. all operations use `@byrow` by default. See [`@subset`](@ref) for details.

Use this function as an alternative to placing the `.` to broadcast row-wise operations.

### Examples

```jldoctest
julia> using DataFramesMeta

julia> df = DataFrame(A=1:5, B=["apple", "pear", "apple", "orange", "pear"])
5×2 DataFrame
 Row │ A      B
     │ Int64  String
─────┼───────────────
   1 │     1  apple
   2 │     2  pear
   3 │     3  apple
   4 │     4  orange
   5 │     5  pear

julia> @rsubset df :A > 3
2×2 DataFrame
 Row │ A      B
     │ Int64  String
─────┼───────────────
   1 │     4  orange
   2 │     5  pear

julia> @rsubset df :A > 3 || :B == "pear"
3×2 DataFrame
  Row │ A      B
      │ Int64  String
 ─────┼───────────────
    1 │     2  pear
    2 │     4  orange
    3 │     5  pear
```
