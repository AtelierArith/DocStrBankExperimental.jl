```
@slice_head(df; n, prop)
```

DataFrameまたはGroupedDataFrameの先頭から行を取得します。

# 引数

  * `df`: 行をスライスする元のデータフレームまたはグループ化されたデータフレーム。
  * `prop`: スライスする行の割合。
  * `n`: データフレームの先頭から取得する行数を指定するオプションの整数引数。デフォルトは1です。

# 例

```jldoctest
julia> df = DataFrame(
           a = [missing, 0.2, missing, missing, 1, missing, 5, 6],
           b = [0.3, 2, missing, 0.3, 6, 5, 7, 7],
           c = [0.2, 0.2, 0.2, missing, 1, missing, 5, 6]);

julia> @chain df begin
         @slice_head(n = 3)
       end 
3×3 DataFrame
 Row │ a          b          c        
     │ Float64?   Float64?   Float64? 
─────┼────────────────────────────────
   1 │ missing          0.3       0.2
   2 │       0.2        2.0       0.2
   3 │ missing    missing         0.2

julia> @chain df begin
         @slice_head(prop = 0.25)
       end 
2×3 DataFrame
 Row │ a          b         c        
     │ Float64?   Float64?  Float64? 
─────┼───────────────────────────────
   1 │ missing         0.3       0.2
   2 │       0.2       2.0       0.2
```
