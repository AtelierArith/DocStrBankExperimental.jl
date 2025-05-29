```
@slice_max(df, column; with_ties = true, n, prop, missing_rm = true)
```

指定された列の最大値を持つ行をDataFrameまたはGroupedDataFrameから取得します。

# 引数

  * `df`: 行をスライスする元のデータフレームまたはグループ化されたデータフレーム。
  * `column`: 最大値をスライスする列。
  * `with_ties`: すべてのタイを表示するかどうか、デフォルトはtrue。falseの場合は最初の行のみ表示されます。
  * `prop`: スライスする行の割合。
  * `n`: 取得する最大行数を指定するオプションの整数引数。with_ties = trueの場合、タイがnを超えるとnは上書きされます。
  * `missing_rm`: デフォルトはtrue、データフレームのスライス割合を決定する際に欠損値をスキップします。

# 例

```jldoctest
julia> df = DataFrame(
           a = [missing, 0.2, missing, missing, 1, missing, 5, 6],
           b = [0.3, 2, missing, 3, 6, 5, 7, 7],
           c = [0.2, 0.2, 0.2, missing, 1, missing, 5, 6]);

julia> @chain df begin
         @slice_max(b)
       end 
2×3 DataFrame
 Row │ a         b         c        
     │ Float64?  Float64?  Float64? 
─────┼──────────────────────────────
   1 │      5.0       7.0       5.0
   2 │      6.0       7.0       6.0

julia> @chain df begin
         @slice_max(b, with_ties = false)
       end 
1×3 DataFrame
 Row │ a         b         c        
     │ Float64?  Float64?  Float64? 
─────┼──────────────────────────────
   1 │      5.0       7.0       5.0

julia> @chain df begin
         @slice_max(b, n = 3)
       end 
3×3 DataFrame
 Row │ a         b         c        
     │ Float64?  Float64?  Float64? 
─────┼──────────────────────────────
   1 │      5.0       7.0       5.0
   2 │      6.0       7.0       6.0
   3 │      1.0       6.0       1.0
   
julia> @chain df begin
         @slice_max(b, prop = 0.5, missing_rm = true)
       end
3×3 DataFrame
 Row │ a         b         c        
     │ Float64?  Float64?  Float64? 
─────┼──────────────────────────────
   1 │      5.0       7.0       5.0
   2 │      6.0       7.0       6.0
   3 │      1.0       6.0       1.0
```
