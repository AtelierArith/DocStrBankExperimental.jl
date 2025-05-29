```
get_meta(table; base, api)
```

指定された `table` のメタデータを取得します。結果は、キー `"TableInfos"`、`"DataProperties"` およびすべての分類を持つ辞書です。

オプションのパラメータは次のとおりです：

  * base::String、OData3 サーバーのベース名
  * api::String、通常のデータのための OData3 サーバーのパス部分
