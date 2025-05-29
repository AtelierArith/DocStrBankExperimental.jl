```
@select(sql_query, columns)
```

SQLテーブルから指定された列を選択します。

# 引数

  * `sql_query::SQLQuery`: 列を選択するためのSQLクエリ。
  * `columns`: 選択する列を指定する式。列は次の方法で指定できます。        - 名前、`table.name`       - セレクタ - `starts_with()`        - 範囲 - `col1:col5`       - `!` 表記で除外

# 例

```jldoctest
julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);

julia> db = connect(duckdb());


julia> df_mem = dt(db, df, "df_view");

julia> @chain df_mem begin
         @select(groups:percent)
         @collect
       end
10×3 DataFrame
 Row │ groups  value  percent 
     │ String  Int64  Float64 
─────┼────────────────────────
   1 │ bb          1      0.1
   2 │ aa          2      0.2
   3 │ bb          3      0.3
   4 │ aa          4      0.4
   5 │ bb          5      0.5
   6 │ aa          1      0.6
   7 │ bb          2      0.7
   8 │ aa          3      0.8
   9 │ bb          4      0.9
  10 │ aa          5      1.0

julia> @chain df_mem begin
         @select(contains("e"))
         @collect
       end
10×2 DataFrame
 Row │ value  percent 
     │ Int64  Float64 
─────┼────────────────
   1 │     1      0.1
   2 │     2      0.2
   3 │     3      0.3
   4 │     4      0.4
   5 │     5      0.5
   6 │     1      0.6
   7 │     2      0.7
   8 │     3      0.8
   9 │     4      0.9
  10 │     5      1.0
```
