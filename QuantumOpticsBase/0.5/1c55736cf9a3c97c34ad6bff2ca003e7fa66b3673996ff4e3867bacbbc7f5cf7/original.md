```
lazytensor_enable_cache(; maxsize::Int = ..., maxrelsize::Real = ...)
```

(Re)-enable the cache for further use; set the maximal size `maxsize` (as number of bytes) or relative size `maxrelsize`, as a fraction between 0 and 1, resulting in `maxsize = floor(Int, maxrelsize * Sys.total_memory())`. Default value is `maxsize = 2^32` bytes, which amounts to 4 gigabytes of memory.
