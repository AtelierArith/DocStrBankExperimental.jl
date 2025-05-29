```
@slice_min(df, column; with_ties = true, n, prop, missing_rm = true)
```

指定された列の最小値を持つ行をDataFrameまたはGroupedDataFrameから取得します。

# 引数

  * `df`: 行をスライスする元のデータフレームまたはグループ化されたデータフレーム。
  * `column`: 最小値をスライスするための列。
  * `with_ties`: すべてのタイを表示するかどうか、デフォルトはtrueで、すべてのタイを表示します。falseの場合は最初の行のみを表示します。
  * `prop`: スライスする行の割合。
  * `n`: 取得する最小行の数を指定するオプションの整数引数。with_ties = trueの場合、タイがnを超えると、nは上書きされます。
  * `missing_rm`: デフォルトはtrueで、データフレームのスライス割合を決定する際に欠損値をスキップします。

# 例

```jldoctest
julia> df = DataFrame(
           a = [missing, 0.2, missing, missing, 1, missing, 5, 6],
           b = [0.3, 2, missing, 0.3, 6, 5, 7, 7],
           c = [0.2, 0.2, 0.2, missing, 1, missing, 5, 6]);

julia> @chain df begin
         @slice_min(b)
       end 
2×3 DataFrame
 Row │ a         b         c         
     │ Float64?  Float64?  Float64?  
─────┼───────────────────────────────
   1 │  missing       0.3        0.2
   2 │  missing       0.3  missing

julia> @chain df begin
         @slice_min(b, with_ties = false)
       end 
1×3 DataFrame
 Row │ a         b         c        
     │ Float64?  Float64?  Float64? 
─────┼──────────────────────────────
   1 │  missing       0.3       0.2

julia> @chain df begin
         @slice_min(b, n = 3)
       end
3×3 DataFrame
 Row │ a          b         c         
     │ Float64?   Float64?  Float64?  
─────┼────────────────────────────────
   1 │ missing         0.3        0.2
   2 │ missing         0.3  missing   
   3 │       0.2       2.0        0.2  
   
julia> @chain df begin
         @slice_min(b, prop = 0.5, missing_rm = true)
       end
3×3 DataFrame
 Row │ a          b         c         
     │ Float64?   Float64?  Float64?  
─────┼────────────────────────────────
   1 │ missing         0.3        0.2
   2 │ missing         0.3  missing   
   3 │       0.2       2.0        0.2
```
