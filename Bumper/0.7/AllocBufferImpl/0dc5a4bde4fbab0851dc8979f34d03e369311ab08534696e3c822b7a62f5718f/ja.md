```
default_buffer(::Type{AllocBuffer}) -> AllocBuffer{Vector{UInt8}}
```

現在のタスクローカルのデフォルト `AllocBuffer` を返します。現在のタスクに存在しない場合は、自動的に作成されます。現在、`AllocBuffer{Vector{UInt8}}` のみを作成でき、作成されるメモリサイズ（1048576バイト）を調整することはできません。
