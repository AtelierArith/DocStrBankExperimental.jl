```
@slice_sample(df, [n = 1, prop, replace = false])
```

DataFrame `df` または GroupedDataFrame の各グループからランダムに行をサンプリングします。デフォルトでは 1 行を返します。キーワード引数として行数 (`n`) または行の割合 (`prop`) のいずれかを指定する必要があります。

# 引数

  * `df`: 行をサンプリングする元のデータフレームまたはグループ化されたデータフレーム。
  * `n`: サンプリングする行数。デフォルトは `1`。
  * `prop`: サンプリングする行の割合。
  * `replace`: 置換ありでサンプリングするかどうか。デフォルトは `false`。

# 例

```julia
julia> df = DataFrame(a = 1:10, b = 11:20);

julia> using StableRNGs, Random

julia> rng = StableRNG(1);

julia> Random.seed!(rng, 1);

julia> @chain df begin 
         @slice_sample(n = 5)
       end
5×2 DataFrame
 Row │ a      b     
     │ Int64  Int64 
─────┼──────────────
   1 │     6     16
   2 │     1     11
   3 │     5     15
   4 │     4     14
   5 │     8     18

julia> @chain df begin 
         @slice_sample(n = 5, replace = true)
       end
5×2 DataFrame
 Row │ a      b     
     │ Int64  Int64 
─────┼──────────────
   1 │     7     17
   2 │     2     12
   3 │     1     11
   4 │     4     14
   5 │     2     12

julia> @chain df begin 
         @slice_sample(prop = 0.5)
       end
5×2 DataFrame
 Row │ a      b     
     │ Int64  Int64 
─────┼──────────────
   1 │     6     16
   2 │     7     17
   3 │     5     15
   4 │     9     19
   5 │     2     12

julia> @chain df begin 
         @slice_sample(prop = 0.5, replace = true)
       end
5×2 DataFrame
 Row │ a      b     
     │ Int64  Int64 
─────┼──────────────
   1 │    10     20
   2 │     4     14
   3 │     9     19
   4 │     9     19
   5 │     8     18
```

```
@slice_sample(sql_query, n)
```

SQL テーブルから指定された行数をランダムに選択します。

# 引数

  * `sql_query::SQLQuery`: サンプリングする SQL クエリ
  * `n`: ランダムに選択する行数。

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
