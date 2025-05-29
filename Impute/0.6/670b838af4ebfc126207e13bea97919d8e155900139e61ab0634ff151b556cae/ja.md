```
impute!(table, imp; cols=nothing) -> table
```

テーブル内のデータを1列ずつ値を補完することによって補完します。これが望ましい動作でない場合は、カスタム補完メソッドがこのメソッドをオーバーロードする必要があります。

# 引数

  * `imp::Imputor`: 使用する補完メソッド
  * `table`: 補完するデータ

# キーワード引数

  * `cols`: 補完する列（デフォルトはすべての列を補完する）

# 戻り値

  * 補完された値を持つ入力 `data`

# 例

```jldoctest
julia> using DataFrames; using Impute: Interpolate, impute


julia> df = DataFrame(:a => [1.0, 2.0, missing, missing, 5.0], :b => [1.1, 2.2, 3.3, missing, 5.5])
5×2 DataFrame
 Row │ a          b
     │ Float64?   Float64?
─────┼──────────────────────
   1 │       1.0        1.1
   2 │       2.0        2.2
   3 │ missing          3.3
   4 │ missing    missing
   5 │       5.0        5.5

julia> impute(df, Interpolate())
5×2 DataFrame
 Row │ a         b
     │ Float64?  Float64?
─────┼────────────────────
   1 │      1.0       1.1
   2 │      2.0       2.2
   3 │      3.0       3.3
   4 │      4.0       4.4
   5 │      5.0       5.5
```
