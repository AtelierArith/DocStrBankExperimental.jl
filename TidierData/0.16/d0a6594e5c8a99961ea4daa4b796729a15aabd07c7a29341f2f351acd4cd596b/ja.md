```
case_when(condition => return_value)
case_when(condition_1 => return_value_1, condition_2 => return_value_2, ...)
```

最初に`true`に評価される`condition`に対応する`return_value`を返します。

最も特定的な条件は最初にリストされ、最も一般的な条件は最後にリストされるべきです。条件がどれも`true`に評価されない場合、`missing`値が返されます。

# 引数

  * `condition`: `true`、`false`、または`missing`に評価される条件。
  * `return_value`: 条件が`true`の場合に返す値。

# 例

```jldoctest
julia> df = DataFrame(a = [1, 2, missing, 4, 5]);

julia> @chain df begin
         @mutate(b = case_when(a > 4  =>  "hi",
                               a > 2  =>  "medium",
                               a > 0  =>  "low"))
       end
5×2 DataFrame
 Row │ a        b       
     │ Int64?   String? 
─────┼──────────────────
   1 │       1  low
   2 │       2  low
   3 │ missing  missing 
   4 │       4  medium
   5 │       5  hi

julia> @chain df begin
         @mutate(b = case_when(a > 4  =>  "hi",
                               a > 2  =>  "medium",
                               a > 0  =>  "low",
                               true   =>  "unknown"))
       end
5×2 DataFrame
 Row │ a        b       
     │ Int64?   String  
─────┼──────────────────
   1 │       1  low
   2 │       2  low
   3 │ missing  unknown
   4 │       4  medium
   5 │       5  hi

julia> @chain df begin
         @mutate(b = case_when(a >= 3  =>  3,
                               true    =>  a))
       end
5×2 DataFrame
 Row │ a        b       
     │ Int64?   Int64?  
─────┼──────────────────
   1 │       1        1
   2 │       2        2
   3 │ missing  missing 
   4 │       4        3
   5 │       5        3

julia> @chain df begin
         @mutate(b = case_when(a >= 3        =>  3,
                               ismissing(a)  =>  0,
                               true          =>  a))
       end
5×2 DataFrame
 Row │ a        b     
     │ Int64?   Int64 
─────┼────────────────
   1 │       1      1
   2 │       2      2
   3 │ missing      0
   4 │       4      3
   5 │       5      3
```
