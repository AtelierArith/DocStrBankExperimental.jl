```
across(variable[s], function[s])
```

複数の変数に関数を適用します。複数の変数または関数を指定する場合は、それらをタプルとして認識されるように括弧で囲んでください。

この関数は、TidierData.jl マクロの内部でのみ呼び出すべきです。

# 引数

  * `variable[s]`: 引用されていない変数、または複数の場合は引用されていない変数のタプル。
  * `function[s]`: 関数、または複数の場合は関数のタプル。

# 例

```jldoctest
julia> df = DataFrame(a = 'a':'e', b = 1:5, c = 11:15);

julia> @chain df begin
         @summarize(across(b, minimum))
       end
1×1 DataFrame
 Row │ b_minimum 
     │ Int64     
─────┼───────────
   1 │         1

julia> @chain df begin
         @summarize(across(where(is_number), minimum))
       end
1×2 DataFrame
 Row │ b_minimum  c_minimum 
     │ Int64      Int64     
─────┼──────────────────────
   1 │         1         11

julia> @chain df begin
         @summarize(across((b,c), (minimum, maximum)))
       end
1×4 DataFrame
 Row │ b_minimum  c_minimum  b_maximum  c_maximum 
     │ Int64      Int64      Int64      Int64     
─────┼────────────────────────────────────────────
   1 │         1         11          5         15

julia> @chain df begin
         @mutate(across((b,c), (minimum, maximum)))
       end
5×7 DataFrame
 Row │ a     b      c      b_minimum  c_minimum  b_maximum  c_maximum 
     │ Char  Int64  Int64  Int64      Int64      Int64      Int64     
─────┼────────────────────────────────────────────────────────────────
   1 │ a         1     11          1         11          5         15
   2 │ b         2     12          1         11          5         15
   3 │ c         3     13          1         11          5         15
   4 │ d         4     14          1         11          5         15
   5 │ e         5     15          1         11          5         15

julia> @chain df begin
         @mutate(across((b, starts_with("c")), (minimum, maximum)))
       end
5×7 DataFrame
 Row │ a     b      c      b_minimum  c_minimum  b_maximum  c_maximum 
     │ Char  Int64  Int64  Int64      Int64      Int64      Int64     
─────┼────────────────────────────────────────────────────────────────
   1 │ a         1     11          1         11          5         15
   2 │ b         2     12          1         11          5         15
   3 │ c         3     13          1         11          5         15
   4 │ d         4     14          1         11          5         15
   5 │ e         5     15          1         11          5         15
```
