```
   @summary(sql_query)
```

DuckDBを使用してテーブルまたはファイルの要約統計を取得します（最大、最小、Q1、Q2、Q3、平均、標準偏差、カウント、ユニーク）

# 引数

  * `sql_query`: 要約するSQLテーブルまたはファイル

# 例

```jldoctest
julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);

julia> db = connect(duckdb());

julia> @chain dt(db, df, "df_view") begin
        @summary
        @collect
       end;
```
