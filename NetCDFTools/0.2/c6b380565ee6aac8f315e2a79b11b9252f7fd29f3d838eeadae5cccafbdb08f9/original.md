```
split_chunk(n::Int, nchunk=4; chunk=nothing, ratio_small::Real=0.5)
```

# Arguments

  * `ratio_small`: The minimum ratio of the last chunk to the maximum length of chunks.

如果最后一个块的小于该比例，则将最后两个块合并。
