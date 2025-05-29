```
get_data(server, dataset, parameters, tmin, tmax; format="csv")
```

指定された `dataset` と `parameters` に対して、時間範囲 `[tmin, tmax]` 内の HAPI `server` からデータとメタデータを取得します。

サポートされているデータ形式: "csv", "binary", "json"。
