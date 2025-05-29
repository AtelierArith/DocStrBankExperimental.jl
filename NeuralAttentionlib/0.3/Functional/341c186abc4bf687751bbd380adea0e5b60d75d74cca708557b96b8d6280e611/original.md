```
multihead_qkv_attention(head, q, k, v, mask=nothing)
```

Multihead version of [`naive_qkv_attention`](@ref). The core operation for implement a regular transformer layer.
