```
UA_STRING(s::AbstractString)::Ptr{UA_String}
```

は`s`から`UA_String`オブジェクトを作成します。メモリはCによって割り当てられ、`UA_String_delete(x::Ptr{UA_String})`でクリーンアップする必要があります。
