```
distinct(df, exprs...)
```

DataFrameの異なる行を返します。

列や式が提供されていない場合、すべての列にわたるユニークな行が返されます。それ以外の場合、提供された列や式に基づいてユニークな行が決定され、その後すべての列が返されます。

# 引数

  * `df`: DataFrame。
  * `exprs...`: カンマで区切られた1つ以上の未引用の変数名。変数名は、`x:y`のようにデータ内の位置としても使用でき、変数の範囲を選択できます。

# 例

```jldoctest
julia> df = DataFrame(a = repeat('a':'e', inner = 2), b = repeat(1:5, 2), c = 11:20);
  
julia> @chain df @distinct()
10×3 DataFrame
 Row │ a     b      c     
     │ Char  Int64  Int64 
─────┼────────────────────
   1 │ a         1     11
   2 │ a         2     12
   3 │ b         3     13
   4 │ b         4     14
   5 │ c         5     15
   6 │ c         1     16
   7 │ d         2     17
   8 │ d         3     18
   9 │ e         4     19
  10 │ e         5     20

julia> @chain df @distinct(a)
5×3 DataFrame
 Row │ a     b      c     
     │ Char  Int64  Int64 
─────┼────────────────────
   1 │ a         1     11
   2 │ b         3     13
   3 │ c         5     15
   4 │ d         2     17
   5 │ e         4     19

julia> @chain df begin
         @distinct(starts_with("a"))
       end
5×3 DataFrame
 Row │ a     b      c     
     │ Char  Int64  Int64 
─────┼────────────────────
   1 │ a         1     11
   2 │ b         3     13
   3 │ c         5     15
   4 │ d         2     17
   5 │ e         4     19

julia> @chain df begin
         @distinct(a, b)
       end
10×3 DataFrame
 Row │ a     b      c     
     │ Char  Int64  Int64 
─────┼────────────────────
   1 │ a         1     11
   2 │ a         2     12
   3 │ b         3     13
   4 │ b         4     14
   5 │ c         5     15
   6 │ c         1     16
   7 │ d         2     17
   8 │ d         3     18
   9 │ e         4     19
  10 │ e         5     20
```

```
@distinct(sql_query, columns...)
```

指定された列に基づいて異なる行を選択します。DistinctはTidierDataとSQL、したがってTidierDBで異なる動作をします。Distinctは、与えられた列のみを選択します（または、与えられた列がない場合はすべて）。

# 引数

`sql_query::SQLQuery`: 操作するSQLクエリ。`columns`: ユニーク性を決定する列。列が指定されていない場合、すべての列が異なる行を特定するために使用されます。

# 例

```jldoctest
julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);

julia> db = connect(duckdb());


julia> @chain dt(db, df, "df_view") begin
         @distinct(value)
         @arrange(value)
         @collect
       end
5×1 DataFrame
 Row │ value 
     │ Int64 
─────┼───────
   1 │     1
   2 │     2
   3 │     3
   4 │     4
   5 │     5

julia> @chain dt(db, df, "df_view") begin
         @distinct
         @arrange(id)
         @collect
       end
10×4 DataFrame
 Row │ id      groups  value  percent 
     │ String  String  Int64  Float64 
─────┼────────────────────────────────
   1 │ AA      bb          1      0.1
   2 │ AB      aa          2      0.2
   3 │ AC      bb          3      0.3
   4 │ AD      aa          4      0.4
   5 │ AE      bb          5      0.5
   6 │ AF      aa          1      0.6
   7 │ AG      bb          2      0.7
   8 │ AH      aa          3      0.8
   9 │ AI      bb          4      0.9
  10 │ AJ      aa          5      1.0
```
