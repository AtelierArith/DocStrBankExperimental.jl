```
   @summarize(sql_query, exprs...; _by)
```

SQLテーブルの指定された列を集約および要約します。

# 引数

  * `sql_query::SQLQuery`: 要約するSQLクエリ
  * `exprs`: 集約および要約操作を定義する式。これには、平均、合計、カウントなどの単純な集約や、既存の列の値を含むより複雑な式を指定できます。
  * `_by`: マクロ呼び出しで集約のためのグループ化を可能にする単一の列名または列のベクトルをサポートするオプションの引数

# 例

```jldoctest
julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);

julia> db = connect(duckdb());


julia> @chain dt(db, df, "df_view") begin
         @group_by(groups)
         @summarise(across((ends_with("e"), starts_with("p")), (mean, sum)))
         @arrange(groups)
         @collect
       end
2×5 DataFrame
 Row │ groups  value_mean  percent_mean  value_sum  percent_sum 
     │ String  Float64     Float64       Int128     Float64     
─────┼──────────────────────────────────────────────────────────
   1 │ aa             3.0           0.6         15          3.0
   2 │ bb             3.0           0.5         15          2.5

julia> @chain dt(db, df, "df_view") begin
         @group_by(groups)
         @summarise(test = sum(percent), n = n())
         @arrange(groups)
         @collect
       end
2×3 DataFrame
 Row │ groups  test     n     
     │ String  Float64  Int64 
─────┼────────────────────────
   1 │ aa          3.0      5
   2 │ bb          2.5      5

julia> @chain dt(db, df, "df_view") begin
                @summarise(test = sum(percent), n = n(), _by = groups)
                @arrange(groups)
                @collect
              end
2×3 DataFrame
 Row │ groups  test     n     
     │ String  Float64  Int64 
─────┼────────────────────────
   1 │ aa          3.0      5
   2 │ bb          2.5      5
```
