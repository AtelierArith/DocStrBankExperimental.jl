```
bea_parameterlist(dataset::String; user_id = USER_ID) -> DataFrame
```

`dataset`のパラメータ名と属性の`DataFrame`を返します。

例：

```julia
# ユーザーIDは ~/.beadatarc に保存されています
julia> bea_parameterlist("NIPA")
5×3 DataFrames.DataFrame. Omitted printing of 1 columns
│ Row │ ParameterName │ ParameterDescription                                           │
│     │ String        │ String                                                         │
├─────┼───────────────┼────────────────────────────────────────────────────────────────┤
│ 1   │ Frequency     │ A - 年次, Q-四半期, M-月次                                     │
│ 2   │ ShowMillions  │ 百万ドルデータを返すべきであることを示すフラグ。               │
│ 3   │ TableID       │ 標準NIPAテーブル識別子                                        │
│ 4   │ TableName     │ 新しいNIPAテーブル識別子                                      │
│ 5   │ Year          │ 取得するデータの年のリスト（Xはすべて）                       │
```
