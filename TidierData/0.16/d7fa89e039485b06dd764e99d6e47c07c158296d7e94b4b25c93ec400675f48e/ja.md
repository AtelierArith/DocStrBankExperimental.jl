```
@summarize(df, exprs...)
@summarise(df, exprs...)
```

入力のDataFrameまたはGroupedDataFrameからすべての観測値を集約した1行の新しいDataFrameを作成します。

# 引数

  * `df`: DataFrame。
  * `exprs...`: `new_variable = function(old_variable)`のペア。`function()`は単一の値を返す集約関数である必要があります。

# 例

```jldoctest
julia> df = DataFrame(a = 'a':'e', b = 1:5, c = 11:15);

julia> @chain df begin
         @summarize(mean_b = mean(b),
                    median_b = median(b))
       end
1×2 DataFrame
 Row │ mean_b   median_b 
     │ Float64  Float64  
─────┼───────────────────
   1 │     3.0       3.0

julia> @chain df begin
         @summarize begin
           mean_b = mean(b)
           median_b = median(b)
         end
       end
1×2 DataFrame
 Row │ mean_b   median_b 
     │ Float64  Float64  
─────┼───────────────────
   1 │     3.0       3.0 

julia> @chain df begin
         @summarise(mean_b = mean(b), median_b = median(b))
       end
1×2 DataFrame
 Row │ mean_b   median_b 
     │ Float64  Float64  
─────┼───────────────────
   1 │     3.0       3.0
   
julia> @chain df begin
         @summarize(across((b,c), (minimum, maximum)))
       end
1×4 DataFrame
 Row │ b_minimum  c_minimum  b_maximum  c_maximum 
     │ Int64      Int64      Int64      Int64     
─────┼────────────────────────────────────────────
   1 │         1         11          5         15

julia> @chain df begin
         @summarize(across(where(is_number), minimum))
       end
1×2 DataFrame
 Row │ b_minimum  c_minimum 
     │ Int64      Int64     
─────┼──────────────────────
   1 │         1         11
```
