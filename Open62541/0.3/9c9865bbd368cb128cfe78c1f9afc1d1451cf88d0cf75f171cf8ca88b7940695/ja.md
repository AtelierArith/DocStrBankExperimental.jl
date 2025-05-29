```
UA_BYTESTRING(s::AbstractString)::Ptr{UA_String}
```

は`s`から`UA_ByteString`オブジェクトを作成します。メモリはCによって割り当てられ、`UA_ByteString_delete(x::Ptr{UA_ByteString})`でクリーンアップする必要があります。
