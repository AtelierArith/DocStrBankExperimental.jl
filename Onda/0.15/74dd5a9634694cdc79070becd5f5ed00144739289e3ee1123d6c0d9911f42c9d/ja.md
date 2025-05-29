```
serializing_lpcm_stream(format::AbstractLPCMFormat, io)
```

`io` に直接 LPCM シリアル化を可能にする `stream::AbstractLPCMStream` を返します。これは [`serialize_lpcm`](@ref) を介して行われます。

`stream` は使用後に [`finalize_lpcm_stream`](@ref) を介して最終化される必要があることに注意してください。`stream` が最終化されるまで、`io` は `stream` の内部状態の一部と見なされ、他のプロセスによって直接操作されるべきではありません。
