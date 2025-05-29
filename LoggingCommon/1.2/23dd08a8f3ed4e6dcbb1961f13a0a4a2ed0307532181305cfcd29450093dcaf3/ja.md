```
log_record_data([KeyType], kv_pairs; [exclude=()]) -> LogRecordData
```

入力の `key::KeyType => value` ペアから `LogRecordData` を返します。

`KeyType` が提供されていない場合、非空の `kv_pairs` のセットから推測されます。
