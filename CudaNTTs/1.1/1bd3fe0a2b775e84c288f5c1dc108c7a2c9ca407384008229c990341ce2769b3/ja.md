```
struct INTTPlan{T<:Union{Int32, Int64, UInt32, UInt64}}
```

NTTを実行するために必要なすべての情報を含む構造体。`INTTPlan(n, p, npru)`を通じて直接構築するか、`plan_ntt()`を参照してください。
