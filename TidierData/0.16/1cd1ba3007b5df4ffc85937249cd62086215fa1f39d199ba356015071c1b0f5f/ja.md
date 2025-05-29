```
@transmute(df, exprs...)
```

計算された列のみを持つ新しいDataFrameを作成します。

# 引数

  * `df`: DataFrame。
  * `exprs...`: `new_variable = values`構文を使用して新しい列を追加するか、既存の列の値を置き換えます。

# 例

```jldoctest
julia> df = DataFrame(a = 'a':'e', b = 1:5, c = 11:15);

julia> @chain df begin
         @transmute(d = b + c)
       end
5×1 DataFrame
 Row │ d     
     │ Int64 
─────┼───────
   1 │    12
   2 │    14
   3 │    16
   4 │    18
   5 │    20
```
