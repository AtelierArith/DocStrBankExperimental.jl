```
dataproperty(io, label)
```

`io::JSeis` からラベル `label::String` のデータプロパティ（データプロパティはトレースごとではなくファイルごとに関連付けられています）を取得します。例えば、`dataproperty(jsopen("data.js"), "FREQUENCY")`。
