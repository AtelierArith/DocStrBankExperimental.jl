```
databuf_set_filled(p_databuf::Ptr{databuf_t}, block_id::Int)
```

指定されたデータブロックを埋められたものとして設定します。ブロックがすでに埋められている場合はエラーを返します。

関連: [`databuf_wait_filled`](@ref), [`databuf_wait_free`](@ref), [`databuf_set_free`](@ref)
