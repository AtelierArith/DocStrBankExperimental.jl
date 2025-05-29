```
where(function)
```

関数が列のすべての値に対して `true` を返す列を選択します。

この関数は、TidierData.jl マクロの内部でのみ呼び出すべきです。

# 引数

  * `function`: 真偽値を返す述語関数（`true` または `false` を返す関数）。

# 例

```jldoctest
julia> df = DataFrame(a = 'a':'e', b = 1:5, c = 11:15);

julia> @chain df begin
         @select(where(is_number))
       end
5×2 DataFrame
 Row │ b      c     
     │ Int64  Int64 
─────┼──────────────
   1 │     1     11
   2 │     2     12
   3 │     3     13
   4 │     4     14
   5 │     5     15

julia> @chain df begin
         @summarize(across(where(is_number), minimum))
       end
1×2 DataFrame
 Row │ b_minimum  c_minimum 
     │ Int64      Int64     
─────┼──────────────────────
   1 │         1         11

julia> @chain df begin
         @mutate(across(where(is_number), minimum))
       end
5×5 DataFrame
 Row │ a     b      c      b_minimum  c_minimum 
     │ Char  Int64  Int64  Int64      Int64     
─────┼──────────────────────────────────────────
   1 │ a         1     11          1         11
   2 │ b         2     12          1         11
   3 │ c         3     13          1         11
   4 │ d         4     14          1         11
   5 │ e         5     15          1         11

julia> df = DataFrame(a = repeat('a':'e', inner = 3),
                      b = 1:15,
                      c = 16:30,
                      d = 31:45);

julia> @chain df begin
         @group_by(a)
         @summarize(across(where(is_number), mean))
       end
5×4 DataFrame
 Row │ a     b_mean   c_mean   d_mean  
     │ Char  Float64  Float64  Float64 
─────┼─────────────────────────────────
   1 │ a         2.0     17.0     32.0
   2 │ b         5.0     20.0     35.0
   3 │ c         8.0     23.0     38.0
   4 │ d        11.0     26.0     41.0
   5 │ e        14.0     29.0     44.0
```
