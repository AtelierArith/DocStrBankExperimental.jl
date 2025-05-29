```
@rename(df, exprs...)
```

DataFrame内の個々の列名を変更します。ユーザーは`@select()`を使用して列をリネームおよび選択することもできます。

# 引数

  * `df`: DataFrame。
  * `exprs...`: `new_name = old_name`構文を使用して選択した列の名前を変更します。

# 例

```jldoctest
julia> df = DataFrame(a = 'a':'e', b = 1:5, c = 11:15);

julia> @chain df begin
         @rename(d = b, e = c)
       end
5×3 DataFrame
 Row │ a     d      e     
     │ Char  Int64  Int64 
─────┼────────────────────
   1 │ a         1     11
   2 │ b         2     12
   3 │ c         3     13
   4 │ d         4     14
   5 │ e         5     15
```
