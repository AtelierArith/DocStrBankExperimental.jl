```
databuf_set_free(p_databuf::Ptr{databuf_t}, block_id::Int)
```

Set the given block of data as free. Return an error if the block is already free.

See also: [`databuf_wait_filled`](@ref), [`databuf_wait_free`](@ref), [`databuf_set_filled`](@ref)
