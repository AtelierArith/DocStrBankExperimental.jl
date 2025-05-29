```
is_thread_safe(::Union{Codec, DecodeOptions, EncodeOptions})::Bool
```

複数のスレッドで同時にエンコードまたはデコードするためにオプションを使用することが安全であれば `true` を返します。
