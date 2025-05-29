```
   @summary(df, cols...)
```

数値列に対して、Q1、Q3、最小値、最大値、平均、中央値、欠損値の数を含むデータフレームを返します。

# 引数

  * 'df': データフレーム
  * `cols`: サマリーを実行する列。この引数はオプションで、指定しない場合はすべての数値列に対してサマリーが実行されます。

# 例

```jldoctest
julia> df = DataFrame(a = [1, 2, 3, 4, 5],
                      b = [missing, 7, 8, 9, 10],
                      c = [11, missing, 13, 14, missing],
                      d = [16.1, 17.2, 18.3, 19.4, 20.5],
                      e = ["a", "a", "a", "a", "a"]);

julia> @summary(df);

julia> @summary(df, (b:d));

julia> @chain df begin
         @summary(b:d)
       end;
```

```
   @summary(sql_query)
```

DuckDBを使用してテーブルまたはファイルの要約統計を取得します（最大、最小、Q1、Q2、Q3、平均、標準偏差、カウント、ユニーク）。

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
