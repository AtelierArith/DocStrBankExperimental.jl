```
summarize(o::CausalTable)
```

`CausalTable`オブジェクト内のデータを、その`summaries`属性に格納されたNetworkSummaryオブジェクトに従って要約します。

# 引数

  * `o::CausalTable`: 要約される`CausalTable`オブジェクト。

# 戻り値

  * 元のデータと要約データが統合された新しい`CausalTable`オブジェクト。
