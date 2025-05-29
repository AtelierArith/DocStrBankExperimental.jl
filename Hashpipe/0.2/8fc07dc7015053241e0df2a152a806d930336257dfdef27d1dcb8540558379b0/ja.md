```
databuf_set_free(p_databuf::Ptr{databuf_t}, block_id::Int)
```

指定されたデータブロックを解放済みとして設定します。ブロックがすでに解放されている場合はエラーを返します。

関連情報: [`databuf_wait_filled`](@ref), [`databuf_wait_free`](@ref), [`databuf_set_filled`](@ref)
