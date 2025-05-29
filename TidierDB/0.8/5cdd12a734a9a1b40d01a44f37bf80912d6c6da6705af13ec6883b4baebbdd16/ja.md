@pivot*longer(df, names*from, values_from)

SQL_queryを長くするために形を変え、行数を増やし、列数を減らします。

# 引数

  * `sql_query`: SQLクエリ
  * `cols`: より長い形式にピボットする列。複数の列を選択できます。
  * `names_from`: オプションで、デフォルトは変数。新しく作成される列の名前で、その値には入力DataFrameの列名が含まれます。
  * `values_from`: オプションで、デフォルトは値。入力DataFrameのセル値を含む新しく作成される列の名前です。

# 例

```jldoctest
julia> df = DataFrame(id = [1, 2], A = [1, 3], B = [2, 4]);

julia> db = connect(duckdb()); df_wide = dt(db, df, "df");

julia> @collect @pivot_longer(df_wide, A:B)
4×3 DataFrame
 Row │ id     variable  value 
     │ Int64  String    Int64 
─────┼────────────────────────
   1 │     1  A             1
   2 │     2  A             3
   3 │     1  B             2
   4 │     2  B             4

julia> @collect @pivot_longer(df_wide, A:B, names_to = "letter", values_to = "number")
4×3 DataFrame
 Row │ id     letter  number 
     │ Int64  String  Int64  
─────┼───────────────────────
   1 │     1  A            1
   2 │     2  A            3
   3 │     1  B            2
   4 │     2  B            4
```
