```
@rename(df, exprs...)
```

DataFrame内の個々の列名を変更します。ユーザーは`@select()`を使用して列をリネームおよび選択することもできます。

# 引数

  * `df`: DataFrame。
  * `exprs...`: 選択した列をリネームするために`new_name = old_name`構文を使用します。

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

```
@rename(sql_query, renamings...)
```

SQLクエリ内の1つ以上の列をリネームします。

# 引数

-`sql_query`: 操作するSQLクエリ。 -`renamings`: 新しい名前 = 古い名前として指定された1つ以上の古いおよび新しい列名のペア 

# 例

```jldoctest
julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);

julia> db = connect(duckdb());


julia> @chain dt(db, df, "df_view") begin
       @rename(new_name = percent)
       @collect
       end
10×4 DataFrame
 Row │ id      groups  value  new_name 
     │ String  String  Int64  Float64  
─────┼─────────────────────────────────
   1 │ AA      bb          1       0.1
   2 │ AB      aa          2       0.2
   3 │ AC      bb          3       0.3
   4 │ AD      aa          4       0.4
   5 │ AE      bb          5       0.5
   6 │ AF      aa          1       0.6
   7 │ AG      bb          2       0.7
   8 │ AH      aa          3       0.8
   9 │ AI      bb          4       0.9
  10 │ AJ      aa          5       1.0
```
