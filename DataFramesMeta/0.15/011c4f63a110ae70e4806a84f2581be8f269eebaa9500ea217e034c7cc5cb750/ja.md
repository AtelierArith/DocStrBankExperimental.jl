```
@rorderby(d, args...)
```

`@orderby`の行単位バージョン、すなわちすべての操作はデフォルトで`@byrow`を使用します。詳細については[`@orderby`](@ref)を参照してください。

この関数は、行単位の操作をブロードキャストするために`.`を置く代わりに使用します。

### 例

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
