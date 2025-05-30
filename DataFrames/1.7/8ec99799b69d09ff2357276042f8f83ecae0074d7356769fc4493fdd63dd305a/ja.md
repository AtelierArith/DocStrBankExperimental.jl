```
SubDataFrame{<:AbstractDataFrame, <:AbstractIndex, <:AbstractVector{Int}} <: AbstractDataFrame
```

`AbstractDataFrame`のビューです。行と列のコレクションが指定された場合、`AbstractDataFrame`の`view`関数を呼び出すことで返されます。

`SubDataFrame`は`AbstractDataFrame`であるため、ほとんどのDataFrame関数が機能することを期待してください。そのようなメソッドには、`describe`、`summary`、`nrow`、`size`、`by`、`stack`、および`join`が含まれます。

親データフレームの列の選択が`:`（コロン）として渡されると、`SubDataFrame`は常に親からすべての列を持ち、作成後に追加または削除されてもそのままです。

# 例

```jldoctest
julia> df = DataFrame(a=repeat([1, 2, 3, 4], outer=[2]),
                      b=repeat([2, 1], outer=[4]),
                      c=1:8)
8×3 DataFrame
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      2      1
   2 │     2      1      2
   3 │     3      2      3
   4 │     4      1      4
   5 │     1      2      5
   6 │     2      1      6
   7 │     3      2      7
   8 │     4      1      8

julia> sdf1 = view(df, :, 2:3) # 列のサブセット
8×2 SubDataFrame
 Row │ b      c
     │ Int64  Int64
─────┼──────────────
   1 │     2      1
   2 │     1      2
   3 │     2      3
   4 │     1      4
   5 │     2      5
   6 │     1      6
   7 │     2      7
   8 │     1      8

julia> sdf2 = @view df[end:-1:1, [1, 3]]  # 行と列のサブセット
8×2 SubDataFrame
 Row │ a      c
     │ Int64  Int64
─────┼──────────────
   1 │     4      8
   2 │     3      7
   3 │     2      6
   4 │     1      5
   5 │     4      4
   6 │     3      3
   7 │     2      2
   8 │     1      1

julia> sdf3 = groupby(df, :a)[1]  # GroupedDataFrameのインデックスはSubDataFrameを返す
2×3 SubDataFrame
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      2      1
   2 │     1      2      5
```
