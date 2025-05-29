```
LimitedExchangeArea <: Area
```

`LimitedExchangeArea`は、提供されたリソースの各個別の運用期間において輸出が制限されるエリアです。これは、エリアが複数の他のエリアと結合されている場合に、総輸出能力を制限する必要があるときに必要です。

# フィールド

  * **`id`** はエリアの名前/識別子です。
  * **`name`** はエリアの名前です。
  * **`lon::Real`** はエリアの経度位置です。
  * **`lat::Real`** はエリアの緯度位置です。
  * **`node::Availability`** はエリア内の異なるリソースをルーティングする`Availability`ノードです。
  * **`limit::Dict{<:EMB.Resource, <:TimeProfile}`** は他のエリアと交換できるリソースの量です。
