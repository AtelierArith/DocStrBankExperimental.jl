```
@transmute(df, exprs...)
```

計算された列のみを持つ新しいDataFrameを作成します。

# 引数

  * `df`: DataFrame。
  * `exprs...`: `new_variable = values`構文を使用して新しい列を追加するか、既存の列の値を置き換えます。

# 例

```jldoctest
julia> df = DataFrame(a = 'a':'e', b = 1:5, c = 11:15);

julia> @chain df begin
         @transmute(d = b + c)
       end
5×1 DataFrame
 Row │ d     
     │ Int64 
─────┼───────
   1 │    12
   2 │    14
   3 │    16
   4 │    18
   5 │    20
```

```
@transmute(sql_query, exprs...; _by, _frame, _order)
```

新しい列を追加するか、既存の列を修正することによってSQLテーブルを変換します。`@mutate`とは異なり、`@transmute`は変換またはグループ化の`=`の左側にある列のみを保持します。

# 引数

  * `sql_query::SQLQuery`: 操作するSQLクエリ。
  * `exprs`: テーブルを変異させるための式。新しい列を追加するか、既存の列を`column_name = expression`構文を使用して修正できます。ここで、式は既存の列を含むことができます。
  * `_by`: マクロ呼び出しでの変換のためにグループ化を許可する単一の列名または列のベクトルをサポートするオプションの引数
  * `_frame`: `@mutate`内でウィンドウフレームを決定できるオプションの引数。単一の数字または数字のタプルをサポートします。`desc()`プレフィックスをサポートします
  * `_order`: `@mutate`内でウィンドウの順序を決定できるオプションの引数。単一の列または名前のベクトルをサポートします

# 例

```jldoctest
julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);

julia> db = connect(duckdb());

julia> @chain dt(db, df, "df_view") begin
         @transmute(value = value * 4, new_col = percent^2)
         @collect
       end
10×2 DataFrame
 Row │ value  new_col 
     │ Int64  Float64 
─────┼────────────────
   1 │     4     0.01
   2 │     8     0.04
   3 │    12     0.09
   4 │    16     0.16
   5 │    20     0.25
   6 │     4     0.36
   7 │     8     0.49
   8 │    12     0.64
   9 │    16     0.81
  10 │    20     1.0

julia> @chain dt(db, df, "df_view") begin
         @transmute(max = maximum(value), _by = groups)
         @collect
       end
10×2 DataFrame
 Row │ groups  max   
     │ String  Int64 
─────┼───────────────
   1 │ aa          5
   2 │ aa          5
   3 │ aa          5
   4 │ aa          5
   5 │ aa          5
   6 │ bb          5
   7 │ bb          5
   8 │ bb          5
   9 │ bb          5
  10 │ bb          5
```
