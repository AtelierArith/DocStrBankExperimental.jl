```
isshuffled,isdeflated,deflate_level = deflate(v::Variable)
```

Return compression information of the variable `v`. If shuffle is `true`, then shuffling (byte interlacing) is activated. If deflate is `true`, then the data chunks (see `chunking`) are compressed using the compression level `deflate_level` (0 means no compression and 9 means maximum compression).
