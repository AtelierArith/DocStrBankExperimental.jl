```
DiskCache(path)
```

`DiskCache{K,V}(path)` constructs a cache with keys of type `K` and values of type `V`, mapped to the filesystem `path` using `serialize` and `deserialize`. `DiskCache` behaves like `Dict` by default, but `DiskCache{K,V,D}` behaves like `D`, an `AbstractDict{K, V}`.

A `DiskCache` supports fast reads of keys already on chip and slow writes of new keys to disk, but does not support modification of existing keys. While writes to existing keys will raise an error, it is always safe to call `get!`.
