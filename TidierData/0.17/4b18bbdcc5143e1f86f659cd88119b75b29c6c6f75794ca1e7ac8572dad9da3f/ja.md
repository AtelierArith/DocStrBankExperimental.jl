```
if_else(condition, yes, no, [miss])
```

`condition`が`true`の場合は`yes`の値を返し、`condition`が`false`の場合は`no`の値を返します。`miss`が指定されている場合、`condition`が`missing`の値を含むときに提供された`miss`の値が返されます。`miss`が指定されていない場合、返される値は明示的な`missing`の値になります。

# 引数

  * `condition`: `true`、`false`、または`missing`に評価される条件。
  * `yes`: 条件が`true`の場合に返す値。
  * `no`: 条件が`false`の場合に返す値。
  * `miss`: オプション。条件が`missing`の場合に返す値。

# 例

```jldoctest
julia> df = DataFrame(a = [1, 2, missing, 4, 5]);

julia> @chain df begin
         @mutate(b = if_else(a >= 3, "yes", "no"))
       end
5×2 DataFrame
 Row │ a        b       
     │ Int64?   String? 
─────┼──────────────────
   1 │       1  no
   2 │       2  no
   3 │ missing  missing 
   4 │       4  yes
   5 │       5  yes

julia> @chain df begin
         @mutate(b = if_else(a >= 3, "yes", "no", "unknown"))
       end
5×2 DataFrame
 Row │ a        b       
     │ Int64?   String  
─────┼──────────────────
   1 │       1  no
   2 │       2  no
   3 │ missing  unknown
   4 │       4  yes
   5 │       5  yes

julia> @chain df begin
         @mutate(b = if_else(a >= 3, 3, a))
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
         @mutate(b = if_else(a >= 3, 3, a, 0))
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
