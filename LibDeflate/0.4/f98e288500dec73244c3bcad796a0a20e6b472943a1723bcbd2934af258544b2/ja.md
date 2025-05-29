```
is_valid_extra_data(ptr::Ptr, remaining_bytes::UInt16)::Bool
```

`ptr` が指し示すバイトのチャンクと `remaining_bytes` 以降が "extra" フィールドの有効な gzip メタデータを表しているかどうかを確認します。
