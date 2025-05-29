```
@filter(df, exprs...)
```

DataFrameを部分的に取得し、指定された条件が満たされているDataFrameのコピーを返します。

# 引数

  * `df`: DataFrame。
  * `exprs...`: `true`または`false`を含むベクトルを生成する変換。

# 例

```jldoctest
julia> df = DataFrame(a = 'a':'e', b = 1:5, c = 11:15);

julia> @chain df begin
         @filter(b >= mean(b))
       end
3×3 DataFrame
 Row │ a     b      c     
     │ Char  Int64  Int64 
─────┼────────────────────
   1 │ c         3     13
   2 │ d         4     14
   3 │ e         5     15

julia> @chain df begin
         @filter(b >= 3 && c >= 14)
       end
2×3 DataFrame
 Row │ a     b      c     
     │ Char  Int64  Int64 
─────┼────────────────────
   1 │ d         4     14
   2 │ e         5     15

julia> @chain df begin
         @filter(b in (1, 3))
       end
2×3 DataFrame
 Row │ a     b      c     
     │ Char  Int64  Int64 
─────┼────────────────────
   1 │ a         1     11
   2 │ c         3     13
```
