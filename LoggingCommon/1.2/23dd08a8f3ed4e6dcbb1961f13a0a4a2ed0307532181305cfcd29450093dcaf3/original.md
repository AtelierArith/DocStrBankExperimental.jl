```
log_record_data([KeyType], kv_pairs; [exclude=()]) -> LogRecordData
```

Returns a `LogRecordData` from the input `key::KeyType => value` pairs.

If `KeyType` is not provided, it will be inferred from a set of non-empty `kv_pairs`.
