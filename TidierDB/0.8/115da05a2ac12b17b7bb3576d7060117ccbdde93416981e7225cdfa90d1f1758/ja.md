```
@relocate(sql_query, columns, before = nothing, after = nothing)
```

クエリされたテーブルの列を再配置します。この関数は、指定された列をテーブル内の新しい位置に移動することを可能にします。移動先は、指定されたターゲット列の前または後のいずれかです。`columns`、`before`、および `after` 引数はすべて、tidy選択関数を受け入れます。`before` または `after` のいずれか一方のみを指定する必要があります。どちらも指定されていない場合、選択された列はテーブルの先頭に移動します。

# 引数

  * `sql_query`: SQLクエリ
  * `columns`: 移動する列または列のリスト。
  * `before`: (オプション) 指定された列が移動する前の列または列のリスト。提供されない場合や `nothing` の場合、この引数は無視されます。
  * `after`: (オプション) 指定された列が移動する後の列または列のリスト。提供されない場合や `nothing` の場合、この引数は無視されます。

# 例

```jldoctest
julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);

julia> db = connect(duckdb());


julia> @chain dt(db, df, "df_view") begin 
        @relocate(groups, value, ends_with("d"), after = percent) 
        @collect
       end
10×4 DataFrame
 Row │ percent  groups  value  id     
     │ Float64  String  Int64  String 
─────┼────────────────────────────────
   1 │     0.1  bb          1  AA
   2 │     0.2  aa          2  AB
   3 │     0.3  bb          3  AC
   4 │     0.4  aa          4  AD
   5 │     0.5  bb          5  AE
   6 │     0.6  aa          1  AF
   7 │     0.7  bb          2  AG
   8 │     0.8  aa          3  AH
   9 │     0.9  bb          4  AI
  10 │     1.0  aa          5  AJ

julia> @chain dt(db, df, "df_view") begin 
        @relocate([:percent, :groups], before = id) 
        @collect
       end
10×4 DataFrame
 Row │ percent  groups  id      value 
     │ Float64  String  String  Int64 
─────┼────────────────────────────────
   1 │     0.1  bb      AA          1
   2 │     0.2  aa      AB          2
   3 │     0.3  bb      AC          3
   4 │     0.4  aa      AD          4
   5 │     0.5  bb      AE          5
   6 │     0.6  aa      AF          1
   7 │     0.7  bb      AG          2
   8 │     0.8  aa      AH          3
   9 │     0.9  bb      AI          4
  10 │     1.0  aa      AJ          5
```
