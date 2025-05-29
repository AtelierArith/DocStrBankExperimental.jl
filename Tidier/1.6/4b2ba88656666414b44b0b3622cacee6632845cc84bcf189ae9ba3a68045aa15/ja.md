```
@count(df, exprs..., [wt], [sort])
```

1つ以上の変数のユニークな値をカウントし、オプションの重み付けを行います。

`@chain df @count(a, b)` は、概ね `@chain df @group_by(a, b) @summarize(n = n())` と同等です。重み付けカウントを行うには `wt` を指定し、要約を `n = n()` から `n = sum(wt)` に切り替えます。グループ化する列が提供されている場合、結果はグループ化されていないデータフレームとなり、これはRの `tidyverse` とは若干異なる動作です。

# 引数

  * `df`: DataFrame または GroupedDataFrame。
  * `exprs...`: カンマで区切られた列名。
  * `wt`: オプションのパラメータ。行をカウントするのではなく、提供された `wt` 変数の合計を計算するために使用されます。
  * `sort`: デフォルトは `false`。結果を `n` の高い順から低い順にソートするかどうか。

# 例

```jldoctest
julia> df = DataFrame(a = vcat(repeat(["a"], inner = 3),
                           repeat(["b"], inner = 3),
                           repeat(["c"], inner = 1),
                           missing),
                      b = 1:8)
8×2 DataFrame
 Row │ a        b     
     │ String?  Int64 
─────┼────────────────
   1 │ a            1
   2 │ a            2
   3 │ a            3
   4 │ b            4
   5 │ b            5
   6 │ b            6
   7 │ c            7
   8 │ missing      8

julia> @chain df @count()
1×1 DataFrame
 Row │ n     
     │ Int64 
─────┼───────
   1 │     8

julia> @chain df begin
         @count(a)
       end
4×2 DataFrame
 Row │ a        n     
     │ String?  Int64 
─────┼────────────────
   1 │ a            3
   2 │ b            3
   3 │ c            1
   4 │ missing      1

julia> @chain df begin
         @count(a, wt = b)
       end
4×2 DataFrame
 Row │ a        n     
     │ String?  Int64 
─────┼────────────────
   1 │ a            6
   2 │ b           15
   3 │ c            7
   4 │ missing      8

julia> @chain df begin
         @count(a, wt = b, sort = true)
       end
4×2 DataFrame
 Row │ a        n     
     │ String?  Int64 
─────┼────────────────
   1 │ b           15
   2 │ missing      8
   3 │ c            7
   4 │ a            6

julia> @chain df begin
         @count(a)
         @count(n)
       end 
2×2 DataFrame
 Row │ n      nn    
     │ Int64  Int64 
─────┼──────────────
   1 │     3      2
   2 │     1      2      
```

```
@count(sql_query, columns...)
```

指定された列でグループ化された行数をカウントします。

# 引数

  * `sql_query::SQLQuery`: 操作するSQLクエリ。
  * `columns`: カウントする前にグループ化する列。列が指定されていない場合、クエリ内のすべての行をカウントします。

# 例

```jldoctest
julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);

julia> db = connect(duckdb());

julia> @chain dt(db, df, "df_view") begin
         @count(groups)
         @arrange(groups)
         @collect
       end
2×2 DataFrame
 Row │ groups  n     
     │ String  Int64 
─────┼───────────────
   1 │ aa          5
   2 │ bb          5
```
