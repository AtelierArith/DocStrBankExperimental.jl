```
bea_table(dataset::String, TableName::String, frequency::String,
    startyear::Int, endyear::Int; user_id = USER_ID) -> BeaTable
```

`TableName`のデータとメタデータを持つ[`BeaTable`](@ref)を返します。`startyear`と`endyear`の両方に整数値`0`を渡すと、テーブルのすべての利用可能な年を取得できます。データ値は、`BeaTable`構造体の`data_values`フィールドを通じてアクセスされる`DataFrame`で返されます。

`TableName`引数は、要求されたテーブルのAPI `TableName`パラメータ値を指します。これらは[`bea_parametervalues`](@ref)メソッドを使用して見つけることができます。

例：NIPAデータセットのテーブル1.1.6を、四半期ごとに、2015年から2018年まで取得する場合。

```julia
# User ID stored in ~/.beadatarc
julia> nipa116 = bea_table("NIPA", "T10106", "Q", 2015, 2018)
BEA Table
Dataset:   NIPA
Table No.: 1.1.6
Title:     実質国内総生産、連鎖ドル
Metric:    連鎖ドル
Units:     10億連鎖（2012）ドル
Frequency: Q
Dates:     2015 - 2018
Revised:   2019年8月29日
```
