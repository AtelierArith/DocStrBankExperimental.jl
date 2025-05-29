```
@nest(df, new_column = nesting_columns)
```

複数の列がデータフレーム内の1つまたは複数の新しい列にネストされます。

# 引数

  * `df`: データフレーム
  * `new_column`: 新しい列名
  * `nesting_columns`: new_columnにネストされる列

# 例

```jldoctest
julia> df = DataFrame(a = repeat('a':'e', inner = 3),
                      b = 1:15,
                      c_1 = 16:30,
                      c_2 = 31:45);

julia> @nest(df, data = b:c_2)
5×2 DataFrame
 Row │ a     data          
     │ Char  DataFrame     
─────┼─────────────────────
   1 │ a     3×3 DataFrame 
   2 │ b     3×3 DataFrame 
   3 │ c     3×3 DataFrame 
   4 │ d     3×3 DataFrame 
   5 │ e     3×3 DataFrame 

julia> @nest(df, data_1 = b, data_2 = starts_with("c"))
5×3 DataFrame
 Row │ a     data_1         data_2        
     │ Char  DataFrame      DataFrame     
─────┼────────────────────────────────────
   1 │ a     3×1 DataFrame  3×2 DataFrame 
   2 │ b     3×1 DataFrame  3×2 DataFrame 
   3 │ c     3×1 DataFrame  3×2 DataFrame 
   4 │ d     3×1 DataFrame  3×2 DataFrame 
   5 │ e     3×1 DataFrame  3×2 DataFrame 

julia> @chain df begin
         @nest(data = b:c_2)
         @unnest_longer(data)
       end
15×2 DataFrame
 Row │ a     data                         
     │ Char  NamedTup…                    
─────┼────────────────────────────────────
   1 │ a     (b = 1, c_1 = 16, c_2 = 31)
   2 │ a     (b = 2, c_1 = 17, c_2 = 32)
   3 │ a     (b = 3, c_1 = 18, c_2 = 33)
   4 │ b     (b = 4, c_1 = 19, c_2 = 34)
   5 │ b     (b = 5, c_1 = 20, c_2 = 35)
   6 │ b     (b = 6, c_1 = 21, c_2 = 36)
   7 │ c     (b = 7, c_1 = 22, c_2 = 37)
   8 │ c     (b = 8, c_1 = 23, c_2 = 38)
   9 │ c     (b = 9, c_1 = 24, c_2 = 39)
  10 │ d     (b = 10, c_1 = 25, c_2 = 40)
  11 │ d     (b = 11, c_1 = 26, c_2 = 41)
  12 │ d     (b = 12, c_1 = 27, c_2 = 42)
  13 │ e     (b = 13, c_1 = 28, c_2 = 43)
  14 │ e     (b = 14, c_1 = 29, c_2 = 44)
  15 │ e     (b = 15, c_1 = 30, c_2 = 45)

julia> @chain df begin
         @nest(data = b:c_2)
         @unnest_wider(data)
       end
5×4 DataFrame
 Row │ a     b             c_1           c_2          
     │ Char  Any           Any           Any          
─────┼────────────────────────────────────────────────
   1 │ a     [1, 2, 3]     [16, 17, 18]  [31, 32, 33]
   2 │ b     [4, 5, 6]     [19, 20, 21]  [34, 35, 36]
   3 │ c     [7, 8, 9]     [22, 23, 24]  [37, 38, 39]
   4 │ d     [10, 11, 12]  [25, 26, 27]  [40, 41, 42]
   5 │ e     [13, 14, 15]  [28, 29, 30]  [43, 44, 45]

julia> @chain df begin
         @nest(data = -a)
         @unnest_wider(data) # wider first
         @unnest_longer(-a)  # then longer
       end
15×4 DataFrame
 Row │ a     b      c_1    c_2   
     │ Char  Int64  Int64  Int64 
─────┼───────────────────────────
   1 │ a         1     16     31
   2 │ a         2     17     32
   3 │ a         3     18     33
   4 │ b         4     19     34
   5 │ b         5     20     35
   6 │ b         6     21     36
   7 │ c         7     22     37
   8 │ c         8     23     38
   9 │ c         9     24     39
  10 │ d        10     25     40
  11 │ d        11     26     41
  12 │ d        12     27     42
  13 │ e        13     28     43
  14 │ e        14     29     44
  15 │ e        15     30     45

julia> @chain df begin
         @nest(data = -a)
         @unnest_longer(data) # longer first
         @unnest_wider(-a)    # then wider
       end
15×4 DataFrame
 Row │ a     b      c_2    c_1   
     │ Char  Int64  Int64  Int64 
─────┼───────────────────────────
   1 │ a         1     31     16
   2 │ a         2     32     17
   3 │ a         3     33     18
   4 │ b         4     34     19
   5 │ b         5     35     20
   6 │ b         6     36     21
   7 │ c         7     37     22
   8 │ c         8     38     23
   9 │ c         9     39     24
  10 │ d        10     40     25
  11 │ d        11     41     26
  12 │ d        12     42     27
  13 │ e        13     43     28
  14 │ e        14     44     29
  15 │ e        15     45     30
```
