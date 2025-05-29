```
@rsubset(d, i...; kwargs...)
```

`@subset`の行単位バージョン、すなわちすべての操作はデフォルトで`@byrow`を使用します。詳細については[`@subset`](@ref)を参照してください。

この関数は、行単位の操作をブロードキャストするために`.`を置く代わりに使用します。

### 例

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
