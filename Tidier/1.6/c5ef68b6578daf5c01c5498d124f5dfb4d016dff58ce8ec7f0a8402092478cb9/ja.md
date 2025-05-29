```
   @head(df, value)
```

データフレームまたはグループ化されたデータフレームの各グループの最初の n 行を表示します。

# 引数

  * `df`: データフレーム。
  * `value`: 返される行数。空白の場合はデフォルトで 6 になります。

# 例

```
julia> df = DataFrame(a = vcat(repeat(["a"], inner = 4),
                                  repeat(["b"], inner = 4)),
                             b = 1:8)
8×2 DataFrame
 Row │ a       b     
     │ String  Int64 
─────┼───────────────
   1 │ a           1
   2 │ a           2
   3 │ a           3
   4 │ a           4
   5 │ b           5
   6 │ b           6
   7 │ b           7
   8 │ b           8
   
julia> @head(df, 3)
3×2 DataFrame
 Row │ a        b     
     │ String?  Int64 
─────┼────────────────
   1 │ a            1
   2 │ a            2
   3 │ a            3

julia> @head(df)
6×2 DataFrame
 Row │ a       b     
     │ String  Int64 
─────┼───────────────
   1 │ a           1
   2 │ a           2
   3 │ a           3
   4 │ a           4
   5 │ b           5
   6 │ b           6

julia> @chain df begin
         @group_by a
         @head 2
       end
GroupedDataFrame with 2 groups based on key: a
First Group (2 rows): a = "a"
 Row │ a       b     
     │ String  Int64 
─────┼───────────────
   1 │ a           1
   2 │ a           2
⋮
Last Group (2 rows): a = "b"
 Row │ a       b     
     │ String  Int64 
─────┼───────────────
   1 │ b           5
   2 │ b           6
```

```
@head(sql_query, value)
```

指定された値に基づいて返される SQL テーブルの行数を制限します。 SQL の `LIMIT`

# 引数

  * `sql_query`: 操作する SQL クエリ。
  * `value`: 返される行数を制限する数。空白の場合はデフォルトで 6 行になります。

# 例

```jldoctest
julia> db = connect(duckdb());

julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);
                     

julia> @chain dt(db, df, "df_view") begin
        @head(1) ## 式をサポートします。 ie `3-2` は下の同じ df を返します
        @collect
       end
1×4 DataFrame
 Row │ id      groups  value  percent 
     │ String  String  Int64  Float64 
─────┼────────────────────────────────
   1 │ AA      bb          1      0.1
```
