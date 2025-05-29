```
starts_with(prefix)
```

`prefix`で始まるすべての列を選択します。

# 引数

  * `prefix`: 文字列。

# 例

```julia
julia> df = DataFrame(a_1 = 1:5, a_2 = 11:15, b_1 = 21:25);

julia> @chain df begin 
         @select(starts_with("a"))
       end
5×2 DataFrame
 Row │ a_1    a_2   
     │ Int64  Int64 
─────┼──────────────
   1 │     1     11
   2 │     2     12
   3 │     3     13
   4 │     4     14
   5 │     5     15
```
