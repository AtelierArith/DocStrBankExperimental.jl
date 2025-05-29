```
databuf_wait_free(p_databuf::Ptr{databuf_t}, block_id::Int)
```

Wait for the given block of data to be freed.

See also: [`databuf_wait_filled`](@ref), [`databuf_set_filled`](@ref), [`databuf_set_free`](@ref)
