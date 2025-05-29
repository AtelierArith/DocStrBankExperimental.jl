```
deserializing_lpcm_stream(format::AbstractLPCMFormat, io)
```

`io`から直接LPCMのデシリアライズを可能にする`stream::AbstractLPCMStream`を返します。これは[`deserialize_lpcm`](@ref)を介して行われます。

`stream`は使用後に[`finalize_lpcm_stream`](@ref)を介して最終化される必要があります。`stream`が最終化されるまで、`io`は`stream`の内部状態の一部と見なされ、他のプロセスによって直接操作されるべきではありません。
