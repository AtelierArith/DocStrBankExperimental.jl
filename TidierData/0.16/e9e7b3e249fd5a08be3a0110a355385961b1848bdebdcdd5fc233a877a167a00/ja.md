@separate(df, from, into, sep, extra = "merge")

指定された区切り文字に基づいて文字列列を複数の新しい列に分割します。

# 引数

  * `df`: DataFrame
  * `from`: 分割される列
  * `into`: 新しい列名、[]または()をサポート
  * `sep`: 分割に使用する文字列または文字
  * `extra`: "merge"、"warn"、および "drop"。提供される列が不十分な場合、extraは追加のエントリが最終的なものにマージされるか、削除されるかを決定します。"warn"は削除された値に対して警告メッセージを生成します。

# 例

```jldoctest
julia> df = DataFrame(a = ["1-1", "2-2", "3-3-3"]);

julia> @separate(df, a, [b, c, d], "-")
3×3 DataFrame
 Row │ b          c          d          
     │ SubStrin…  SubStrin…  SubStrin…? 
─────┼──────────────────────────────────
   1 │ 1          1          missing    
   2 │ 2          2          missing    
   3 │ 3          3          3

julia> @chain df begin
         @separate(a, (b, c, d), "-")
       end
3×3 DataFrame
 Row │ b          c          d          
     │ SubStrin…  SubStrin…  SubStrin…? 
─────┼──────────────────────────────────
   1 │ 1          1          missing    
   2 │ 2          2          missing    
   3 │ 3          3          3

julia> @separate(df, a, (b, c), "-")
3×2 DataFrame
 Row │ b          c      
     │ SubStrin…  String 
─────┼───────────────────
   1 │ 1          1
   2 │ 2          2
   3 │ 3          3-3

julia> @chain df begin
         @separate(a, (b, c), "-", extra = "drop")
       end
3×2 DataFrame
 Row │ b          c         
     │ SubStrin…  SubStrin… 
─────┼──────────────────────
   1 │ 1          1
   2 │ 2          2
   3 │ 3          3

```
