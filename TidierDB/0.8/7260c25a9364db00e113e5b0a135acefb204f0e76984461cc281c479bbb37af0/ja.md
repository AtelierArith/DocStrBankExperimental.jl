```
@slice_sample(sql_query, n)
```

SQLテーブルから指定された数の行をランダムに選択します。

# 引数

  * `sql_query::SQLQuery`: サンプリングするSQLクエリ
  * `n`: ランダムに選択する行の数。

# 例

```jldoctest
julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);

julia> db = connect(duckdb());


julia> @chain dt(db, df, "df_view") begin
         @group_by(groups)
         @slice_sample(n = 2)
         @collect
       end;

julia> @chain dt(db, df, "df_view") begin
       @slice_sample()
       @collect
       end;
```
