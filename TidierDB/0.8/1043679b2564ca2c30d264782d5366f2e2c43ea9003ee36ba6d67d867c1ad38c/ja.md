```
@filter(sql_query, conditions...)
```

指定された条件に基づいてSQLテーブルの行をフィルタリングします。

# 引数

  * `sql_query::SQLQuery`: 行をフィルタリングするためのSQLクエリ。
  * `conditions`: 行が出力に含まれるために満たす必要がある条件を指定する式。                   式が`true`に評価される行が結果に含まれます。                   複数の条件は論理演算子（`&&`, `||`）を使用して組み合わせることができます。 `@filter`は自動的に                   条件がWHEREに属するかHAVINGに属するかを検出します。

一時的には、複数の条件をフィルタリングする際にbeginとendを使用するのが最適です。（例2参照）

# 例

```jldoctest
julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);

julia> db = connect(duckdb());


julia> @chain dt(db, df, "df_view") begin
         @filter(percent > .5)
         @collect
       end
5×4 DataFrame
 Row │ id      groups  value  percent 
     │ String  String  Int64  Float64 
─────┼────────────────────────────────
   1 │ AF      aa          1      0.6
   2 │ AG      bb          2      0.7
   3 │ AH      aa          3      0.8
   4 │ AI      bb          4      0.9
   5 │ AJ      aa          5      1.0

julia> @chain dt(db, df, "df_view") begin
         @group_by(groups)
         @summarise(mean = mean(percent))
         @filter begin 
           groups == "bb" || # このように論理演算子を使用することもできます
           mean > .5
         end
         @arrange(groups)
         @collect
       end
2×2 DataFrame
 Row │ groups  mean    
     │ String  Float64 
─────┼─────────────────
   1 │ aa          0.6
   2 │ bb          0.5

julia> q = @chain dt(db, df, "df_view") @summarize(mean = mean(value));

julia> @eval @chain dt(db, df, "df_view") begin
         @filter(value < $q) 
         @collect
       end
4×4 DataFrame
 Row │ id      groups  value  percent 
     │ String  String  Int64  Float64 
─────┼────────────────────────────────
   1 │ AA      bb          1      0.1
   2 │ AB      aa          2      0.2
   3 │ AF      aa          1      0.6
   4 │ AG      bb          2      0.7
```
