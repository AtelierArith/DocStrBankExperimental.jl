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
           a = ["a", "b", "a", "b", "a", "b", "a", "a"],
           b = [0.3, 2, missing, 0.3, 6, 5, 7, 7],
           c = [0.2, 0.2, 0.2, missing, 1, missing, 5, 6]);

julia> @chain df begin
         @slice_head(prop = .3)
       end 
2×3 DataFrame
 Row │ a       b         c        
     │ String  Float64?  Float64? 
─────┼────────────────────────────
   1 │ a            0.3       0.2
   2 │ b            2.0       0.2

julia> @chain df begin
         @group_by(a)
         @slice_head(n = 2)
         @ungroup
       end 
4×3 DataFrame
 Row │ a       b          c         
     │ String  Float64?   Float64?  
─────┼──────────────────────────────
   1 │ a             0.3        0.2
   2 │ a       missing          0.2
   3 │ b             2.0        0.2
   4 │ b             0.3  missing   
```
