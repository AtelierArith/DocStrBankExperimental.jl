```
struct DecodedSizeError <: Exception
DecodedSizeError(max_size, decoded_size)
```

データをデコードできません。デコードされたサイズが `max_size` より大きいか、予想より小さいためです。デコードされたサイズが不明な場合、`decoded_size` は `nothing` です。
