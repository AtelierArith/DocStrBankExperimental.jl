```
distinct(df, exprs...)
```

DataFrameの異なる行を返します。

列や式が提供されていない場合、すべての列にわたるユニークな行が返されます。それ以外の場合、提供された列や式に基づいてユニークな行が決定され、その後すべての列が返されます。

# 引数

  * `df`: DataFrame。
  * `exprs...`: カンマで区切られた1つ以上の引用されていない変数名。変数名は、`x:y`のようにデータ内の位置としても使用でき、変数の範囲を選択できます。

# 例

```jldoctest
julia> df = DataFrame(a = repeat('a':'e', inner = 2), b = repeat(1:5, 2), c = 11:20);
  
julia> @chain df @distinct()
10×3 DataFrame
 Row │ a     b      c     
     │ Char  Int64  Int64 
─────┼────────────────────
   1 │ a         1     11
   2 │ a         2     12
   3 │ b         3     13
   4 │ b         4     14
   5 │ c         5     15
   6 │ c         1     16
   7 │ d         2     17
   8 │ d         3     18
   9 │ e         4     19
  10 │ e         5     20

julia> @chain df @distinct(a)
5×3 DataFrame
 Row │ a     b      c     
     │ Char  Int64  Int64 
─────┼────────────────────
   1 │ a         1     11
   2 │ b         3     13
   3 │ c         5     15
   4 │ d         2     17
   5 │ e         4     19

julia> @chain df begin
         @distinct(starts_with("a"))
       end
5×3 DataFrame
 Row │ a     b      c     
     │ Char  Int64  Int64 
─────┼────────────────────
   1 │ a         1     11
   2 │ b         3     13
   3 │ c         5     15
   4 │ d         2     17
   5 │ e         4     19

julia> @chain df begin
         @distinct(a, b)
       end
10×3 DataFrame
 Row │ a     b      c     
     │ Char  Int64  Int64 
─────┼────────────────────
   1 │ a         1     11
   2 │ a         2     12
   3 │ b         3     13
   4 │ b         4     14
   5 │ c         5     15
   6 │ c         1     16
   7 │ d         2     17
   8 │ d         3     18
   9 │ e         4     19
  10 │ e         5     20
```
