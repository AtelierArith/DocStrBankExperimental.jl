```
lazytensor_enable_cache(; maxsize::Int = ..., maxrelsize::Real = ...)
```

キャッシュを再度有効にして、さらなる使用のために最大サイズ `maxsize`（バイト数）または相対サイズ `maxrelsize` を設定します。相対サイズは0と1の間の分数で、結果として `maxsize = floor(Int, maxrelsize * Sys.total_memory())` になります。デフォルト値は `maxsize = 2^32` バイトで、これは4ギガバイトのメモリに相当します。
