```
everything()
```

残りのすべての列を選択します。

# 引数

  * なし

# 例

```julia
julia> df = DataFrame(a_1 = 1:5, a_2 = 11:15, b_1 = 21:25);

julia> @chain df begin 
         @select(b_1, everything())
       end
5×3 DataFrame
 Row │ b_1    a_1    a_2   
     │ Int64  Int64  Int64 
─────┼─────────────────────
   1 │    21      1     11
   2 │    22      2     12
   3 │    23      3     13
   4 │    24      4     14
   5 │    25      5     15
```
